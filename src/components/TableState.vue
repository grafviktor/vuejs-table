<template>
<dl class="list">
  <div v-for="cell in Object.keys(cells)" :key="cell" class="list-item">
    <dt>{{cell}} :</dt>
    <dd>{{cells[cell] ? `${cells[cell]}px` : 'X'}}</dd>
  </div>
</dl>
</template>

<script>
export default {
  props : ['cells']
}
</script>

<style>
  .list {
    box-sizing    : border-box;

    margin        : -40px 20px 20px;
    padding       : 10px;
    width         : 200px;

    border-radius : 5px;
    border        : 1px solid lightgray;
    box-shadow    : 2px 2px 6px gray;
  }

  .list-item {
    display               : grid;
    grid-template-columns : 100px 100px;
  }

  .list-item:nth-child(odd) {
    padding : 2px;

    border-radius    : 2px;
    background-color : #eee;
  }

  dt,
  dd {
    margin  : 0 !important;
    padding : 0 !important;
  }
</style>