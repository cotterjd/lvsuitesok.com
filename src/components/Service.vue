<template>
  <div>
    <h2>{{title}}</h2>
    <p class="w-96 h-64 grid items-center">{{ blurb }}</p>
    <div class="service-image-container">
      <img :src="images[0]" alt="Venue Image" width="400px" />
    </div>
    <button class="button" @click="openGallery">Gallery</button>

    <div v-show="isOpen" class="modal" @click="closeGallery">
      <span class="close" @click="closeGallery">×</span>
      <div class="modal-content gallery">
        <img v-for="src in images" :key="src" :src="src" alt="Gallery Image" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false,
      images: [],
    };
  },
  props: [`title`, `blurb`],
  methods: {
    openGallery() {
      console.log('Opening gallery');
      this.isOpen = true;
    },
    closeGallery() {
      this.isOpen = false;
    },
  },
  mounted() {
    if (this.title === `Venue`) {
      this.images = [
        '/src/assets/images/venue_cropped.jpg',
        '/src/assets/images/venue/venue1.jpg',
        '/src/assets/images/venue/venue2.jpg',
        '/src/assets/images/venue/venue3.jpg',
        '/src/assets/images/venue/venue4.jpg',
        '/src/assets/images/venue/venue7.jpg',
      ]
    } else if (this.title === `House`) {
      this.images = [
        '/src/assets/images/house_cropped.jpg',
        '/src/assets/images/house/house1.jpg',
        '/src/assets/images/house/house2.jpg',
        '/src/assets/images/house/house3.jpg',
        '/src/assets/images/house/house4.jpg',
        '/src/assets/images/house/house5.jpg',
      ]
    } else if (this.title === `Room`) {
      this.images = [
        '/src/assets/images/room_cropped.jpg',
        '/src/assets/images/house/house14.jpg',
        '/src/assets/images/house/house19.jpg',
        '/src/assets/images/house/house25.jpg',
        '/src/assets/images/house/house26.jpg',
        '/src/assets/images/house/house27.jpg',
        '/src/assets/images/house/house28.jpg',
        '/src/assets/images/house/house29.jpg',
        '/src/assets/images/house/house30.jpg',
        '/src/assets/images/house/house31.jpg',
        '/src/assets/images/house/house33.jpg',
        '/src/assets/images/house/house34.jpg',
        '/src/assets/images/house/house38.jpg',
        '/src/assets/images/house/house39.jpg',
      ]
    }
  }
};
</script>

<style> 
.button {
  background-color: #b3d6f2;
  color: white;
  padding: 15px 20px;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  font-size: 16px;
  margin: 10px 0;
  text-align: center;
  width: 100%;
  font-weight: bold;
}
h2 {
  font-size: 2rem;
  font-weight: bold;
}
.modal {
  display: block;
  position: fixed;
  z-index: 1;
  left: 5%;
  top: 10px;
  width: 90%;
  height: 100%;
  overflow: auto;
  background-color: rgb(0,0,0);
  background-color: rgba(0,0,0,0.9);
}

.modal-content {
  padding: 20px;
  width: 80%;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
  gap: 10px;
  margin: auto;
}

.close {
  color: white;
  float: right;
  font-size: 40px;
  font-weight: bold;
  margin-right: 20px
}

.close:hover,
.close:focus {
  color: #bbb;
  text-decoration: none;
  cursor: pointer;
}

.gallery img {
  width: 100%;
  height: auto;
}

.service-image-container {
}
</style>
