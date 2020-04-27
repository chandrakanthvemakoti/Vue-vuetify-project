<template>
   <v-container>
       <v-app>
       <div>
           <h1>MY DASHBOARD </h1>
       </div>
      <Table :headers="headers" :search="search"  :desserts="desserts"/>
       </v-app>
       
   </v-container>
</template>


<script>
import Table from './Table.vue'
  export default {
    data () {
      return {
        search: '',
        headers: [
          {
            text: 'Name',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          { text: 'Email', value: 'email' },
          { text: 'Role', value: 'role' },
          
        ],
        desserts: [
          {
            name: '',
            email:'',
            role:''
          },
          ],
      }
    },

    components:{
        Table
    }
  }
</script>