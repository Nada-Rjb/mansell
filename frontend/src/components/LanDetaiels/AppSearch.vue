<template>
    <div class="search"></div>
    <section class="hero flow " data-padding="compact">
      <div  id="main">
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
    height: 68px;
    display: flex;
    align-items: center;
    justify-content: start;
    background-color: #D9D9D9;
  }
  .forsearch {
    border-radius: 0.5rem;
    padding: 0.5rem 1rem 0.5rem 0.5rem;
    outline: none;
    border: #D9D9D9 solid 1px;
    width: 60%;
    margin: 0.5rem;
    height: 40px;
  }
  
  .search-icon {
    position: absolute;
    right: 55%;
    top: 50%;
    width: 20px;
    transform: translateY(-50%);
  }
  </style>