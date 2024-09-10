<template>
  <div>
    <button @click="openGallery">Open Gallery</button>

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
      images: [
        '/src/assets/images/venue/venue1.jpg',
        '/src/assets/images/venue/venue2.jpg',
        '/src/assets/images/venue/venue3.jpg',
        '/src/assets/images/venue/venue4.jpg',
        '/src/assets/images/venue/venue7.jpg',
      ],
    };
  },
  methods: {
    openGallery() {
      console.log('Opening gallery');
      this.isOpen = true;
    },
    closeGallery() {
      this.isOpen = false;
    },
  },
};
</script>

<style> 
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
  font-size: 28px;
  font-weight: bold;
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
