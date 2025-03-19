<template>
    <div class="search"></div>
    <section class="hero flow section" data-padding="compact">
      <div class="wrapper" id="main">
        <div class="search-container">
          <input
            type="search"
            name="navSearch"
            id="navSearch"
            class="forsearch"
            placeholder="اسم العميل"
          />
  
          <img
            src="../../assets/imges/search.png"
            alt="Search Icon"
            class="search-icon"
          />
        </div>
      </div>
    </section>
  </template>
  
  <style scoped>
  .search-container {
    position: relative;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .forsearch {
    border-radius: 2rem;
    padding: 0.5rem 1rem 0.5rem 0.5rem;
    outline: none;
    border: #d9d9d9 solid 1px;
    width: 100%;
    height: 40px;
  }
  
  .search-icon {
    position: absolute;
    left: 30px;
    top: 50%;
    width: 20px;
    transform: translateY(-50%);
  }
  </style>