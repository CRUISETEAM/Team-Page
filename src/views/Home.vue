<template>
  <div class="home">
    <div class="logo">
      <img src="/images/cruise-logo.png" alt="CRUISE Logo">
    </div>
    <div class="gallery">
      <div v-for="(photo, index) in photos" :key="index" class="photo-container"
        @click="redirectToGithub(photo.githubLink)">
        <div class="content">
          <img :src="`/images/${photo.fileName}`" :alt="photo.altText" class="photo"
            @mouseover="toggleHover(index, true)" @mouseleave="toggleHover(index, false)">
          <p class="name">{{ photo.name }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      photos: [
        { fileName: '동흔.png', altText: '동흔', name: '백동흔', githubLink: 'https://github.com/beakdongH' },
        { fileName: '민성.png', altText: '민성', name: '김민성', githubLink: 'https://github.com/alstjd223' },
        { fileName: '윤서.png', altText: '윤서', name: '조윤서', githubLink: 'https://github.com/cys070124' },
        { fileName: '혜성.png', altText: '혜성', name: '문혜성', githubLink: 'https://github.com/moonhyeseong07' },
        { fileName: '희성.png', altText: '희성', name: '신희성', githubLink: 'https://github.com/huise0ng' }
      ]
    }
  },
  methods: {
    redirectToGithub(link) {
      window.open(link, '_blank');
    },
    toggleHover(index, isHover) {
      this.photos[index].isHovered = isHover;
    }
  }
}
</script>

<style scoped>
.home {
  text-align: center;
}

.logo {
  margin-bottom: 20px;
}

.gallery {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.photo-container {
  margin: 10px;
  text-align: center;
}

.content {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.photo {
  width: 220px;
  height: auto;
  transition: transform 0.3s ease;
}

.photo:hover {
  transform: scale(1.1);
}

@font-face {
  font-family: 'KCC Hanbit Gothic';
  src: url('/fonts/KCC_Hanbit.ttf') format('truetype');
}

.name {
  font-family: 'KCC Hanbit Gothic', sans-serif;
  font-size: 14px;
  margin-top: 5px;
}
</style>
