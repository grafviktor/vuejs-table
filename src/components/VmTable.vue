<template>
  <div>
    <a-table bordered :columns="cols" :components="components" :data-source="rows">
      <template v-slot:action>
        <a href="javascript:;">Delete</a>
      </template>
    </a-table>
    <table-state :cells="draggingState" />
  </div>
</template>

<script>
import Vue from 'vue';
import ResizableCell from './ResizableCell.vue';
import TableState from './TableState';

const initDraggingStateMap = cols => {
    const draggingMap = cols.reduce((acc, col) => ({
      ...acc,
      [col.dataIndex] : col.width
    }), {});

    return Vue.observable(draggingMap);
}

export default {
  name: 'VmTable',
  props : [
    'tableRows',
    'tableCols'
  ],
  data() {
    this.components = {
      header : {
        cell : ResizableCell,
      }
    };
    return {
      rows          : this.tableRows,
      cols          : this.tableCols,
      draggingState : initDraggingStateMap(this.tableCols)
    }
  },
  provide () {
    return {
      tableColumns  : this.tableCols,
      draggingState : this.draggingState
    }
  },
  components : {TableState}
};
</script>
<style lang="less">
</style>