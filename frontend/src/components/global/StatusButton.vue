<template>
    <section class="hero flow section" data-padding="compact">
      <div class="wrapper" id="main">
        <div class="transaction-buttons">
          <button :class="['status-button', status]">
            <span class="lable">{{ label }}</span>
            <span :class="['status-icon', status]">
              <span v-if="status === 'success'"><img src="../../assets/imges/correctsign.svg" alt=""></span>
              <span v-else-if="status === 'error'"><img src="../../assets/imges/Wrongsign.svg" alt=""></span>
            </span>
          </button>
        </div>
      </div>
    </section>
  </template>
  <script>
  export default {
    props: {
      label: {
        type: String,
        required: true,
      },
  
      status: {
        type: String,
        default: "success",
      },
    },
  };
  </script>
  <style lang="scss" scoped>
 .status-button {
  width: 30%;
  min-width: 90px;
  max-width: 200px; 
  padding: 0.5rem 1rem;
    height: 40px; 

  @media (min-width: 760px) {
    width: 25%; 
    min-width: 120px;
    max-width: 250px;
    height: 40px; 
  }

  @media (min-width: 1024px) {
    width: 20%;
    min-width: 140px;
    max-width: 280px;
    height: 40px;
  }

  background-color: rgb(49, 49, 46);
  border-radius: var(--border-radius-2);
  color: #f5f5f5;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  border: none;
  font-weight: bold;
  position: relative;

  &.success {
    background-color: #14ae5c;
  }

  &.error {
    background-color: #ec221f;
  }

  &.nothing {
    background-color: red;
  }

  .status-icon {
    width: 23px;
    height: 23px;
    position: absolute;
    top: -15px;
    right: -10px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    font-size: 14px;
  }
}

  
 
  </style>