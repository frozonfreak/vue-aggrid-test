<template>
  <div>
    <ag-grid-vue style="width: 500px; height: 500px;"
                   class="ag-theme-balham"
                   :columnDefs="columnDefs"
                   :rowData="rowData"
                   :cellValueChanged="cellValueChanged"
                   :gridReady="onGridReady"
                   :gridOptions="gridOptions">
      </ag-grid-vue>
      <button @click="changeColor">Change Color</button>
    </div>
</template>

<script>
import {AgGridVue} from "ag-grid-vue";

    export default {
        name: 'App',
        data() {
            return {
                columnDefs: null,
                rowData: null,
                gridApi: null,
                columnApi: null,
                gridOptions: null
            }
        },
        components: {
            AgGridVue
        },
        methods: {
          onGridReady(params) {
                          this.gridApi = params.api;
                          this.columnApi = params.columnApi;
                          console.log(params);
                      },
          cellValueChanged: function(param) {
            console.log(param);
          },
          changeColor: function() {
            var rowNode = this.gridOptions.api.getRowNode(0);
            rowNode.setDataValue('model', 'Toyota');
          }
        },

        beforeMount() {
            this.gridOptions = {};
            this.columnDefs = [
                {headerName: 'Make', field: 'make'},
                {headerName: 'Model', field: 'model',editable:true,
                  cellClassRules: {
                              'rag-green': 'x == "Mondeo"',
                              'rag-red': 'x == "Celica"',
                          }
                },
                {headerName: 'Price', field: 'price'}
            ];

            this.rowData = [
                {id: 1, make: 'Toyota', model: 'Celica', price: 35000},
                {id: 2, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 3, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 4, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 5, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 6, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 7, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 8, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 9, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 10, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 11, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 12, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 13, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 14, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 15, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 16, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 17, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 18, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 19, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 20, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 21, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 22, make: 'Ford', model: 'Mondeo', price: 32000},
                {id: 23, make: 'Porsche', model: 'Boxter', price: 72000}
            ];
        }
    }
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
.rag-red {
    background-color: lightcoral;
}
.rag-green {
    background-color: lightgreen;
}
.rag-amber {
    background-color: lightsalmon;
}

.rag-red-outer .rag-element {
    background-color: lightcoral;
}

.rag-green-outer .rag-element {
    background-color: lightgreen;
}

.rag-amber-outer .rag-element {
    background-color: lightsalmon;
}
</style>
