<template>
  <ag-grid-vue style="width: 2000px; height: 2000px" class="ag-theme-alpine" :columnDefs="columnDefs" :rowData="rowData">
  </ag-grid-vue>
</template>

<script>
import "ag-grid-community/styles//ag-grid.css";
import "ag-grid-community/styles//ag-theme-alpine.css";
import { AgGridVue } from "ag-grid-vue";

export default {
  name: "App",
  components: {
    AgGridVue,
  },
  data() {
    return {
      columnDefs: null,
      rowData: null,
    };
  },
  beforeMount() {
     this.columnDefs = [
       { field: 'id', sortable: true, filter: true },
       { field: 'rank', sortable: true, filter: true },
       { field: 'title', sortable: true, filter: true },
       { field: 'fullTitle', sortable: true, filter: true },
       { field: 'year', sortable: true, filter: true },
       { field: 'image', sortable: true, filter: true },
       { field: 'crew', sortable: true, filter: true },
       { field: 'imDbRating', sortable: true, filter: true },
       { field: 'imDbRatingCount', sortable: true, filter: true },
     ];

     fetch('https://imdb-api.com/en/API/Top250Movies/k_zt6cp48g')
             .then(result => result.json())
             .then(rowData => this.rowData = rowData.items);
   },
}

</script>