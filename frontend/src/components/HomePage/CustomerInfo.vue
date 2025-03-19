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
                <p>مسار الحركه : {{ locationText }} </p>
                <img class="map-icon cursor-pointer" :src="mapImage" alt="Map" @click = "getLocation"/>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  import {FileUploader} from "frappe-ui";
  export default {
    data() {
     return {
      customerImage:"",
      successMapIcon: new URL("@/assets/imges/correctsign.svg", import.meta.url).href, // Success icon
      defaultImage: new URL("@/assets/imges/shop.png", import.meta.url).href, // Correct way to import image
      mapImage: new URL("@/assets/imges/map.png", import.meta.url).href, // Ensure map image loads properly
      location : null,
      error: null,
      locationText: "اضغط على الخريطة للحصول على موقعك",

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

        getLocation() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(
              // Success Callback

          (position) => {
            this.location = {
              lat: position.coords.latitude,
              lng: position.coords.longitude,
            };
            //which converts the coordinates into a human-readable address.
           this.getAddress(this.location.lat, this.location.lng);
            this.mapUrl = `https://maps.googleapis.com/maps/api/staticmap?center=${this.location.lat},${this.location.lng}&zoom=15&size=300x200&markers=color:red%7C${this.location.lat},${this.location.lng}&key=YOUR_GOOGLE_MAPS_API_KEY`;
            this.mapImage = this.successMapIcon;


            console.log("User Location:", this.location);
          },
          (error) => {
             this.error = "فشل في الحصول على الموقع: " + error.message;
             this.locationText = "";
             this.mapImage = this.defaultImage;

          }
        );
      } else {
        this.error = "الموقع غير مدعوم في هذا المتصفح.";
        this.mapImage = this.defaultImage;

      }
    },
  
  async getAddress (latitud,longitude) {
     const apiUrl = `https://nominatim.openstreetmap.org/reverse?lat=${latitud}&lon=${longitude}&format=json&accept-language=ar`;
     try {
      const response = await fetch (apiUrl);
      const data = await response.json();
      if (data.display_name) {
      this.locationText = `📍 ${data.display_name}`;
      }
      else {
                  this.error = "لم يتم العثور على عنوان لهذا الموقع.";

      }
         }catch (error) {
        this.error = "حدث خطأ أثناء جلب العنوان.";

  
      }
    }}
  }

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