<template>
  <div id="app">
    <data-table :header="header" :data="data" :options="{
      columns: columnsCustomization
    }"/>
  </div>
</template>

<script>
import DataTable from './components/DataTable.vue';

export default {
  name: 'app',
  components: {
    DataTable,
  },
  data() {
    return {
      header : ['Product', 'Batch', 'Price', 'Total'],
      data : [['Patanjali', 'WETG76', 76, 80], 
                ['Colgate', 'WET876', 45, 50],
                ['Volini spray gel', 'WRT876', 35, 59]],
      columnsCustomization: [{
        editable: true,
        type: 'text'
      }, {}, {
        editable: true,
        type: 'number'
      }, {}],
    };
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
