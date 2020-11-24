<template>
   <div>
        <Spinner v-if="isLoading"/>
        <Table 
          v-else-if="data"
          :planListHeader="planListHeader" 
          :tableSourceData="data" 
          >
        </Table>
   </div>
</template>

<script>
import Table from './components/Table.vue';
import Spinner from './components/Spinner';
import axios from 'axios';


export default {
  name: 'App',
  components: {
   Table,
   Spinner
  },
  data() {
    return {
    planListHeader:[
      'project_name',
      'developer',
      'main_contractor',
      'address',
      'state',
      'status',
      'sector'
    ],
      isLoading: false,
      error: null,
      data: [],
    }
  },
   methods: {
    loadTableData() {
      this.isLoading = true;
      this.error = null;
      axios
      .get('https://244b8df3-7491-4cfd-a48b-267f19446372.mock.pstmn.io/')
        .then((response) => {
          this.isLoading = false;
          this.data = response.data.data
        })
        .catch(() => {
          this.isLoading = false;
          this.error = 'Failed to fetch data - please try again later.';
        });
    },
  },
  mounted () {
    this.loadTableData();
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
