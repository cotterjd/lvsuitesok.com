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
        // Add more image paths as needed
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
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgb(0,0,0);
  background-color: rgba(0,0,0,0.9);
}

.modal-content {
  margin: 15% auto;
  padding: 20px;
  width: 80%;
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
