<template>
    <section class="hero flow section" data-padding="compact">
      <div class="wrapper" id="main">
        <div class="debt-summary">
          <h3>دائن</h3>
          <p class="amount">156.410 <span class="currency">جنيه</span></p>
        </div>
        <div class="grid-container">
          <div class="info">
            <p class="label">آخر معاملة</p>
            <p class="value">منذ أسبوع</p>
            <p class="date">15-مارس-25</p>
          </div>
  
          <div class="info">
            <p class="label">قيمة آخر معاملة</p>
            <p class="value">1,421 <span class="currency">جنيه مصري</span></p>
          </div>
        </div>
      </div>
    </section>
  </template>
  <style lang="scss">
  .debt-summary {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 1rem;
    .amount {
      font-size: 2.5rem;
      font-weight: bold;
    }
  }
  .grid-container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
    width: 100%;
    margin-top: 1rem;
    align-items: start;
  }
  .info {
    padding-top: 1rem;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 0.2rem;
  }
  
  .label {
    font-size: 0.9rem;
    border-bottom: 2px solid black;
    font-weight: bold;
  }
  
  .value {
    font-size: 1.2rem;
    font-weight: bold;
  }
  
  .date {
    font-size: 0.8rem;
    color: gray;
  }
  </style>