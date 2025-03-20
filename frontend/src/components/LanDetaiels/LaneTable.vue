<template>
    <div class="search"></div>
    <section class="hero flow section" data-padding="compact">
      <div class="wrapper" id="main">
        <div class="search-container">
            <table>
                <tr>
                  <th>اسم العميل</th>
                  <th>الفاتوره</th>
                  <th>الدفع</th>
                  <th>المرور</th>
            
                </tr>
                <tr v-for="(row,rowIndex) in tableData" :key="rowIndex"
                >
                    <td v-for="(cell,cellIndex) in row" :key="cellIndex" :class= "{'success' : cell === 'succeeded' , 'failed' : cell === 'failed'}">
                        <img v-if="cell === 'succeeded'"  src="../../assets/imges/correctsign.svg" alt="succeeded" class="status-icon">
                       <img v-if="cell === 'failed'" src="../../assets/imges/Wrongsign.svg" alt="failed" class="status-icon">
                      
                    </td>

                </tr>
            </table>
        </div>
      </div>
    </section>
  </template>
  <script>
  export default {
    data() {
        return {
        tableData: [
        ["succeeded", "failed", "succeeded", "succeeded"],
        ["succeeded", "failed", "succeeded", "succeeded"],
        ["succeeded", "failed", "succeeded", "succeeded"],
      ],} 
    }   
    }
</script>
  <style scoped>
  table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  text-align: center;
  padding: 0.5rem;
  border-bottom: 2px solid #D9D9D9; 
  border-right: 2px solid #D9D9D9; 
  border-top: none;
}

th:last-child, td:last-child {
  border-left: none ;
}
th:first-child, td:first-child {
  border-right: none ;
}
/* .success {
  background-color: lightgreen;
}

.failed {
  background-color: lightcoral;
} */
.status-icon {
    margin: auto;
    width: 50px;
    height: 50px;
}

  </style>