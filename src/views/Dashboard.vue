<template>
   <v-container>
       <v-app>
       <div>
           <h1>MY DASHBOARD </h1>
       </div>
       <div>
      <Table :headers="headers" :search="search"  :desserts="desserts"/>
      </div>
<div>
  <Formtable @myemit="desserts=$event"/>
</div>

       </v-app>
       
   </v-container>
</template>


<script>
import Formtable from './Formtable.vue';
import Table from './Table.vue';
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
        Table,
        Formtable
    }
  }
</script>