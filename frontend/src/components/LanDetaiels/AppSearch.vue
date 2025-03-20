<template>
    <div class="search"></div>
    <section class="hero flow " data-padding="compact">
      <div class="searchLan">
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
      </div></div>
    </section>
  </template>
  
  <style scoped>
  .searchLan {
  background-color: #D9D9D9;
  height: 68px;


  }
  .search-container {
    position: relative;
    width: 60%;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 68px;


  }
  .forsearch {
    border-radius: 0.5rem;
    padding: 0.5rem 1rem 0.5rem 0.5rem;
    outline: none;
    border: #D9D9D9 solid 1px;
    width: 100%;
    margin: 0.5rem;
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