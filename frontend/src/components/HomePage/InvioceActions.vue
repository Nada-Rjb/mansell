<template>
  <section class="flow section" data-padding="compact">
    <div class="wrapper" id="main">
      <div class="invoice-actions">
        <Button class="show-invoices" @click="() => openQuickview($event)">📄 عرض الفواتير</Button>
        <Button class="upload-invoice">⬆️ رفع الفاتورة</Button>

        
      </div>
    </div>
  </section>
</template>




  <style scoped>
  .section {
    margin-bottom: 1rem;
  }
  .invoice-actions {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 2rem;
  }
  
  @media (min-width: 760px) {
    .invoice-actions {
      flex-direction: row;
      gap: 15rem;
    }
  }
  
  button {
    width: 153px;
    height: 40px;
    border-radius: var(--border-radius-2);
    cursor: pointer;
    font: bolder;
  }
  .show-invoices {
    background-color: #2c2c2c;
    color: #f5f5f5;
    border: 1px solid #2c2c2c;
  }
  .upload-invoice {
    border: 1px solid #d9d9d9;
    color: #1e1e1e;
  }
  .upload-invoice:hover {
    background-color: #e3e3e3;
  }
  .show-invoices:hover {
    background-color: #373737;
  }
  </style>
  <script>
  export default {
    inject: ['Emitter'],
    methods: {
    openQuickview(){
      console.log('Button clicked!');
      this.Emitter.emit('open-quickview');
    }}
  };
  
</script>