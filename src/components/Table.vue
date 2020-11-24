<template>
  <div class="tableWrapper">
    <table  id="fourthTable">   
      <thead>
        <tr>
          <th v-for="col in planListHeader" v-bind:key="col">{{col}}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="row in tableSourceData" v-bind:key="row" >
          <td v-for="col in planListHeader" v-bind:key="col">{{row[col]}}</td>
        </tr>
      </tbody>
   </table>
  </div>
</template>

<script>
export default {
  props: {
    tableSourceData: Array ,
    planListHeader: Object,
    isLoading: Boolean
  },
}
</script>

<style  lang="scss" scoped>
.tableWrapper {
  margin: 0;
  position: relative;
  z-index: 1;
  overflow:auto;
  padding-bottom: 5px;

  table {
    border-collapse: collapse; 
    width: 74%;
    margin: 0 auto;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);

    tbody{ 
      tr{
        border-bottom: 1px  solid #fdfdfd;

          &:nth-child(even) td {
            background: #F8F8F8;
          }

          td:nth-child(6) {
          color: #FFAD25;
          border-radius: 0.3125rem;
          margin: auto;
          padding: 0.5rem;
          width: fit-content;
        }
      }
    
    }
      
    th {
      text-transform: uppercase;
      text-align: left;
      background: #44475C;
      color: #FFF;
      cursor: pointer;
      min-width: 30px;
      font-size: 1rem;
      color: #FFF;
      padding: 15px;
      position: sticky;
      cursor: pointer;
      top: 0;
      white-space: nowrap;

      &:nth-child(1) {
      position: sticky;
      left: 0;
      z-index: 2;
    }
    }
    td {
      color: #344356;
      padding: 0.5rem;
      text-align: left;
    
      &:nth-child(1) {
        border-right: solid 2px #ddd;
        left: 0;
        position: relative;
        top: auto;
        position: sticky;
        z-index: 2;
        background: #fff;
      }
      &:last-child {
      border-right: none;
      }
    } 
  }
}
</style>
