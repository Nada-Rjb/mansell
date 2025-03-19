<template>
    <div class="AppNav">
      <header class="site-header">
        <!-- TO DO: overwrite padding -->
        <div style="margin-inline: 2rem">
          <div class="site-header__inner">
            <img
              src="../../assets/imges/elfateh.jpg"
              alt="El Fateh"
              style="max-inline-size: 60px"
            />
            <button
              area-control="primary-navigation"
              area-expanded="false"
              :class="{ 'menu-active': menuOpen }"
              @click="toggleMenu"
              style="width: 40px; height: 40px"
            >
              <span class="visually-hidden">Menue</span>
              <img
                src="../../assets/imges/hamburger.svg"
                alt="menue"
                style="width: 40px; height: 40px"
              />
            </button>
            <nav
              id="primary-navigation"
              class="primary-nav"
              v-show="!isMobile || menuOpen"
            >
              <ul role="list">
                <li><a href="/">استعلام</a></li>
                <li><a href="/">تفاصيل المسار</a></li>
                <li><a href="/">تفاصيل الموظف</a></li>
                <li v-if="!isMobile">
                  <a href="/" class="logout">تسجيل الخروج</a>
                </li>
              </ul>
              <div v-if="isMobile" class="alone">
                <li><a href="/" class="logout">تسجيل الخروج</a></li>
              </div>
            </nav>
          </div>
        </div>
      </header>
    </div>
  </template>
  <script></script>
  <style lang="scss">
  .no-scroll {
    overflow: hidden;
    height: 100vh;
  }
  
  .skipp-to-header:not(:focus) {
    clip: rect(0 0 0 0);
    clip-path: inset(50%);
    height: 1px;
    overflow: hidden;
    position: absolute;
    white-space: nowrap;
    width: 1px;
  }
  .skipp-to-header {
    position: absolute;
    background-color: var(--background-accent-main);
    padding: 1rem;
    border-radius: var(--border-radius-1);
    position: fixed;
  }
  .site-header {
    padding-block: 0.5rem;
    /*overflow-x: hidden;*/
    overflow-x: clip;
    position: relative;
    border-bottom: #d9d9d9 solid;
  
    a {
      color: var(--clt-black);
    }
    a:hover,
    a:focus-visible {
      color: #f59c5c;
    }
  }
  .site-header__inner {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem 2rem;
    justify-content: space-between;
    align-items: center;
  }
  [area-control="primary-navigation"] {
    background: transparent;
    border: 0;
    cursor: pointer;
    img {
      border-radius: 0;
    }
  }
  [area-control="primary-navigation"] {
    display: none;
  }
  
  .primary-nav {
    ul {
      list-style: none;
      margin-top: 1.2rem;
      padding: 0;
      display: flex;
      position: static;
      flex-wrap: wrap;
      gap: 0.5rem 2rem;
      cursor: pointer;
    }
    a {
      text-decoration: none;
    }
  
    @media (width < 760px) {
      .site-header {
        padding-block: 0.5rem;
        /*overflow-x: hidden;*/
        overflow-x: clip;
        position: relative;
        border-bottom: #d9d9d9 solid;
      }
      height: calc(100vh - 5rem); /* Full height */
      position: hidden;
      display: flex;
      flex-direction: column;
      justify-content: center;
      top: 5rem;
      left: 0;
      font-size: var(--font-size-heading-lg);
      text-align: center;
      align-items: center;
      width: 100%;
      font-size: large;
      background-color: white;
      ul {
        display: flex;
        align-items: center;
        text-align: center;
        flex-direction: column;
        max-width: 400px;
        width: 80%;
        border-radius: var(--border-radius-3);
        padding: 2rem 0;
  
        li {
          background-color: white;
          padding: 1rem;
          border-bottom: 1px solid #ccc;
          align-items: center;
          font-weight: bolder;
          width: 100%;
        }
        li:hover {
          background-color: #f5f5f5;
        }
      }
    }
  
    .logout {
      /* Push to bottom */
      color: red;
      font-weight: bold;
      text-align: center;
      padding: 0.5rem;
      cursor: pointer;
      border-bottom: red solid;
    }
  }
  .menu-active {
    background-color: rgba(
      71,
      69,
      69,
      0.1
    ); /* Light black transparent background */
    border-radius: 50%; /* Make it round */
    transition: background-color 0.3s ease-in-out;
  }
  .alone {
    list-style: none;
    margin-top: 8rem;
  }
  /*any thing that come that is direct sibling */
  @media (width < 760px) {
    [area-control="primary-navigation"] {
      display: block;
    }
    [area-expanded="true"] ~ .primary-nav {
      display: block;
      opacity: 1;
      translate: 0 0;
    }
  }
  </style>
  <script>
  export default {
    data() {
      return {
        menuOpen: false, // Default: Menu is closed
        isMobile: window.innerWidth < 760, // Check initial screen size
      };
    },
    mounted() {
      window.addEventListener("resize", this.checkScreenSize);
    },
    beforeUnmount() {
      window.removeEventListener("resize", this.checkScreenSize);
    },
    methods: {
      checkScreenSize() {
        this.isMobile = window.innerWidth < 760; // Update `isMobile`
        if (!this.isMobile) {
          this.menuOpen = false; // Ensure menu is always visible on large screens
        }
      },
      toggleMenu() {
        if (this.isMobile) {
          this.menuOpen = !this.menuOpen; // Toggle only on small screens
          // Toggle "no-scroll" class on the body to prevent scrolling when the menu is open
  
          document.body.classList.toggle("no-scroll", this.menuOpen);
          console.log("Menu Open:", this.menuOpen); // Debugging: Check console log
        }
      },
    },
  };
  </script>