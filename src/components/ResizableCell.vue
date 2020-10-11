<template>
  <th ref="headerRef" :width="col.width" class="resize-table-th">
    <slot></slot>
    <vue-draggable-resizable
      :key="col.dataIndex"
      class="table-draggable-handle"
      :w="10"
      :x="draggingState[col.dataIndex]"
      axis="x"
      :draggable="true"
      :resizable="false"
      @dragging="onDrag"
      @dragstop="onDragstop"
    />
  </th>
</template>

<script>
import VueDraggableResizable from 'vue-draggable-resizable';

export default {
  data() {
    return {
      headerRef : null,
    }
  },
  computed : {
    col() {
      return this.tableColumns.find(column => this.$attrs.key === column.dataIndex)
    }
  },
  methods : {
    onDrag(x) {
      this.draggingState[this.col.dataIndex] = 0;

      this.col.width = Math.max(x, 1);
    },
    onDragstop () {
      const {width} = this.$refs.headerRef.getBoundingClientRect();

      this.draggingState[this.col.dataIndex] = width;
    }
  },
  components : {
    VueDraggableResizable
  },
  inject: ['tableColumns', 'draggingState']
}
</script>

<style lang="less">
.resize-table-th {
  position: relative;
  .table-draggable-handle {
    height: 100% !important;
    bottom: 0;
    left: auto !important;
    right: -5px;
    cursor: col-resize;
    touch-action: none;
  }
}
</style>