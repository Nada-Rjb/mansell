<template>
    <section class="hero flow section" data-padding="compact">
      <div class="wrapper" id="main">
        <div class="TransactionButtons">
          <StatusButton label="فاتوره" status="error"></StatusButton>
          <StatusButton label="دفع" status="success"></StatusButton>
          <StatusButton label="بواسطه " status=""></StatusButton>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  import StatusButton from "../global/StatusButton.vue";
  export default {
    components: { StatusButton },
  };
  </script>
  <style>
.TransactionButtons {
  display: flex;
  justify-content: space-between; /* Ensures even spacing */
  align-items: center;
    width: 100%;

}
  </style>