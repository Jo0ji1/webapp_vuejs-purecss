<template>
  <div class="gallery-page">
    <h2>Galeria de Imagens</h2>
    <div class="gallery-grid">
      <div class="gallery-card" v-for="(image, index) in images" :key="index">
        <img :src="image.src" :alt="alt" />
        <p>{{ image.alt }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'GalleryPage',
  data() {
    return {
      images: [
        { src: 'https://picsum.photos/300/200?random=101', alt: 'Exemplo Random 101' },
        { src: 'https://picsum.photos/300/200?random=102', alt: 'Exemplo Random 102' },
        { src: 'https://picsum.photos/300/200?random=103', alt: 'Exemplo Random 103' },
        { src: 'https://picsum.photos/300/200?random=104', alt: 'Exemplo Random 104' },
        { src: 'https://picsum.photos/300/200?random=105', alt: 'Exemplo Random 105' },
        { src: 'https://picsum.photos/300/200?random=106', alt: 'Exemplo Random 106' },
        { src: 'https://picsum.photos/300/200?random=107', alt: 'Exemplo Random 107' },
        { src: 'https://picsum.photos/300/200?random=108', alt: 'Exemplo Random 108' }
      ]
    }
  }
}
</script>

<style scoped>
.gallery-page {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px 0;
  color: #fff; /* se o fundo do site for escuro */
}
h2 {
  text-align: center;
  margin-bottom: 20px;
}
.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}
.gallery-card {
  background: #fff;
  padding: 10px;
  text-align: center;
  border-radius: 8px;
  border: 1px solid #ddd;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;
}
.gallery-card:hover {
  transform: scale(1.03);
}
.gallery-card img {
  max-width: 100%;
  border-radius: 4px;
}
.gallery-card p {
  margin-top: 10px;
  color: #333;
}
</style>
