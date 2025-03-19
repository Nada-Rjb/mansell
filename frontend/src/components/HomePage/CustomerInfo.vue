<template>
    <section class="hero flow section" data-padding="compact">
      <div class="wrapper" id="main">
        <div :class="{'customer-img-wrapper' : isdefaultImage, 'no-bg' : !isdefaultImage} " >
         <input  ref="inputimage" v-if="isdefaultImage"  type="file"  @change="uploadImage" capture="environment" accept="image/*" class="upload-btn hidden cursor"/>
        <img :class="{'default-img' : isdefaultImage , 'cursor-pointer' : isdefaultImage} " class="customer-img" :src="customerImage || defaultImage" 
            alt="Customer Image" 
            @error="useDefaultImage"
            @click="openFileSelector" />
        </div>
            <!-- Upload Button (Only Shown if Default Image is Active) -->
        <div class="infomatin">
          <div>
            <h3>اسم العميل</h3>
          </div>
          <div class="info">
            <p>مسار الحركه</p>
          <img class="map-icon" :src="mapImage" alt="Map" />
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    data() {
     return {
      customerImage:"",
      defaultImage: new URL("@/assets/imges/shop.png", import.meta.url).href, // Correct way to import image
      mapImage: new URL("@/assets/imges/map.png", import.meta.url).href, // Ensure map image loads properly
    };
    },
    computed: {
      isdefaultImage () {
        return !this.customerImage;
      }
    },
    methods: {
      //at error in customer image 
      useDefaultImage (event) {
        event.target.src = this.defaultImage
        this.isdefaultImage = true
      },
      uploadImage(event) {
        //upload one image 
        const file = event.target.files[0]
        if (file) {
        console.log("File selected:", file.name, file.size, file.type); // Debugging output
        this.customerImage = URL.createObjectURL(file)
        }},
        
        openFileSelector () {
          this.$refs.inputimage.click();
        },

      
    }
  };
  </script>
  
  <style lang="scss" scoped>
  .section {
    --pading: 0.1rem;
    padding-block: var(--pading);
  }
  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  
  .customer-img-wrapper {
    width: 90%;
    height: 15rem;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #eee;
    border-radius: 10px;
    .no-bg{
        background-color: transparent !important;

    }
    
  }
  .default-img {
  width: 106px !important;
  height: 106px !important;
}
.customer-img {
  width: 20rem;
  aspect-ratio: 1/1;
  height: auto;
  object-fit: cover;
  border-radius: 10px;
}

  .infomatin {
    display: flex;
    flex-direction: column;
    width: 90%;
    padding: 0.5rem;
    gap: 0.1rem;
  }
  .hero {
    align-items: center;
    text-align: start;
  }
  
  .info {
    width: 100%;
    display: flex;
    flex-direction: row;
    gap: 0.5rem;
    justify-content: space-between;
    align-items: center;
    p {
      color: #757575;
    }
  }
  
  .map-icon {
    width: 50px;
    height: 50px;
    align-self: center; /* Keep it aligned */
  }
  .cursor-pointer {
  cursor: pointer;
}
  
  </style>