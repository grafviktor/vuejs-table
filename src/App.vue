<template>
  <vm-table :tableCols="columns" :tableRows="rows"/>
</template>

<script>
import VmTable from './components/VmTable.vue';

const columns = [
  {
    title: 'Date',
    dataIndex: 'date',
    width: 200,
  },
  {
    title: 'Amount',
    dataIndex: 'amount',
    width: 100,
  },
  {
    title: 'Type',
    dataIndex: 'type',
    width: 100,
  },
  {
    title: 'Note',
    dataIndex: 'note',
    width: 100,
  },
  {
    title: 'Action',
    dataIndex: 'action',
    scopedSlots: { customRender: 'action' }
  },
];
const rows = [
  {
    key: 0,
    date: '2018-02-11',
    amount: 120,
    type: 'income',
    note: 'transfer',
  },
  {
    key: 1,
    date: '2018-03-11',
    amount: 243,
    type: 'income',
    note: 'transfer',
  },
  {
    key: 2,
    date: '2018-04-11',
    amount: 98,
    type: 'income',
    note: 'transfer',
  },
];

export default {
  components : {
    VmTable
  },
  data () {
    return {columns, rows}
  }
}
</script>