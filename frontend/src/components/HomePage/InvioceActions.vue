<template>
  <section class="flow section" data-padding="compact">
    <div class="wrapper" id="main">
      <div class="invoice-actions">
        <button class="show-invoices" @click="() => openQuickview($event)"> <img src="../../assets/imges/Trello.svg" alt="Upload" class="icon bg-transparent" />
  <p> رفع الفاتورة</p> </button>
<button class="upload-invoice" >
  <img src="../../assets/imges/Iconupload.svg" alt="Upload" class="icon bg-transparent" />
  <p> رفع الفاتورة</p>
</button>

        
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
  
  Button {
    display: flex;
    flex-direction: row;
    width: 153px;
    height: 40px;
    border-radius: var(--border-radius-2);
    cursor: pointer;
    font: bolder;
  }
 
  .upload-invoice , .show-invoices {
    display: flex;
    flex-direction: row;
    border: 1px solid #d9d9d9;
    color: #1e1e1e;
    gap: 1rem;
    align-items: center;
    justify-content: center;
  }
  .show-invoices {
    background-color: #2c2c2c;
    color: #f5f5f5;
    border: 1px solid #2c2c2c;
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