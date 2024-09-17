<template>
  <div>
    <h2>{{title}}</h2>
    <div class="service-image-container">
      <img v-if="images.length" :src="images[0].src" alt="Venue Image" width="400px" />
    </div>
    <button class="button" @click="openGallery">Gallery</button>
    <p class="w-96 h-64 grid">{{ blurb }}</p>

    <div v-show="isOpen" class="modal" @click="closeGallery">
      <span class="close" @click="closeGallery">×</span>
      <div class="modal-content gallery">
        <img v-for="src in images" :key="src.src" :src="src.src" alt="Gallery Image" />
      </div>
    </div>
  </div>
</template>

<script>
import img_cropped from '../assets/venue_cropped.jpg';
import img1 from '../assets/venue/venue1.jpg';
import img2 from '../assets/venue/venue2.jpg';
import img3 from '../assets/venue/venue3.jpg';
import img4 from '../assets/venue/venue4.jpg';
import img7 from '../assets/venue/venue7.jpg';
import house_cropped from '../assets/house_cropped.jpg';
import house1 from '../assets/house/house1.jpg';
import house2 from '../assets/house/house2.jpg';
import house3 from '../assets/house/house3.jpg';
import house4 from '../assets/house/house4.jpg';
import house5 from '../assets/house/house5.jpg';
import room_cropped from '../assets/room_cropped.jpg';
import room1 from '../assets/house/house14.jpg';
import room2 from '../assets/house/house19.jpg';
import room3 from '../assets/house/house25.jpg';
import room4 from '../assets/house/house26.jpg';
import room5 from '../assets/house/house27.jpg';
import room6 from '../assets/house/house28.jpg';
import room7 from '../assets/house/house29.jpg';
import room8 from '../assets/house/house30.jpg';
import room9 from '../assets/house/house31.jpg';
import room10 from '../assets/house/house33.jpg';
import room11 from '../assets/house/house34.jpg';
import room12 from '../assets/house/house38.jpg';
import room13 from '../assets/house/house39.jpg';

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
        img_cropped,
        img1,
        img2,
        img3,
        img4,
        img7,
      ]
    } 
    else if (this.title === `House`) {
      this.images = [
        house_cropped,
        house1,
        house2,
        house3,
        house4,
        house5,
      ]
    } else if (this.title === `Room`) {
      this.images = [
        room_cropped,
        room1,
        room2,
        room3,
        room4,
        room5,
        room6,
        room7,
        room8,
        room9,
        room10,
        room11,
        room12,
        room13,
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

</style>
