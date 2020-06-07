<template>
  <div id="app">
       <h1>Table Pagination</h1>
       <Tabela v-if="tableData" :theData="tableData" :settings="settings"  :style="{height: '600px'}"/>
  </div>
</template>

<script>
import Tabela from './components/Tabela.vue'

export default {
     components: {Tabela},     
     data() {
        return {
             tableData: undefined,
             settings: [
                 {key: 'photo', title: 'Photo', type: 'image'},
                 {key: 'name', title: 'Name', type: 'text'},
                 {key: 'city', title: 'City', type: 'text'},
                 {key: 'ocuppation', title: 'Ocuppation', type: 'text'},
                 {key: 'date', title: 'Registry', type: 'date'}
             ]
        }
     },
     mounted() {
         this.$axios.get('http://localhost:8081/link')
             .then(({data}) => {
                 this.tableData = data
             })
     }
}
</script>

<style>
body {
  font-family: Helvetica, sans-serif;
  font-weight: 400;
  background-color: #4cb69f;
  color: white;
  
}

h1 {
  font-size: 5rem;
   align-self: center;
   justify-content: center;
   display: flex;
   -webkit-text-stroke-width: 3px;
   -webkit-text-stroke-color: black;
   
}
</style>
