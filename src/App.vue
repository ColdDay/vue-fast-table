<template>
  <div id="app">
    <VueFastTable 
      :data="list"
      :columns="columns"
      :options="options"
       />
  </div>
</template>

<script>
import VueFastTable from './components/VueFastTable.vue'

export default {
  name: 'app',
  components: {
    VueFastTable
  },
  data() {
    return {
      list: [{
        date: 1233
      },{
        date: 4566
      }],
      columns: [],
      options: {
        rowHeight: 60,
      }
    }
  }
}
</script>

<style>

</style>
