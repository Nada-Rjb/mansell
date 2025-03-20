<template>
    <div class="search"></div>
    <section class="hero flow section" data-padding="compact">
      <div class="wrapper" id="main">
        <div class="search-container">
            <table>
                <tr>
                    <th>client Name </th>
                    <th>Invoiced</th>
                    <th>Payment</th>
                    <th>Pass by</th>             
                </tr>
                <tr>
                    <td>succed</td>
                    <td>failed</td>
                    <td>succed</td>
                    <td>succed</td>
                </tr>
                   <tr>
                    <td>succed</td>
                    <td>failed</td>
                    <td>succed</td>
                    <td>succed</td>
                </tr>
                   <tr>
                    <td>succed</td>
                    <td>failed</td>
                    <td>succed</td>
                    <td>succed</td>
                </tr>


            </table>
        </div>
      </div>
    </section>
  </template>
  
  <style scoped>
  table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  text-align: center;
  padding: 0.5rem;
  border-bottom: 1px solid black; 
  border-right: 1px solid black; 
  border-top: none;
}

th:last-child, td:last-child {
  border-left: none ;
}
th:first-child, td:first-child {
  border-right: none ;
}




  </style>