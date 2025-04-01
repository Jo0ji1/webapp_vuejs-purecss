<template>
  <div class="home-page">
    <!-- Carrossel (CSS) -->
    <div class="carousel-container">
      <div class="carousel-slides">
        <img src="https://picsum.photos/1000/400?random=1" alt="Slide 1" />
        <img src="https://picsum.photos/1000/400?random=2" alt="Slide 2" />
        <img src="https://picsum.photos/1000/400?random=3" alt="Slide 3" />
      </div>
    </div>

    <!-- Seção de destaque / texto principal -->
    <section class="welcome-text">
      <h2>Por que usar Vue.js + Pure.css?</h2>
      <p>
        Uma combinação leve, reativa e flexível que permite criar aplicações escaláveis,
        com visual limpo e alta performance.
      </p>
    </section>

    <!-- Relógio -->
    <ClockDisplay />

    <!-- Cards de Destaque (grid) -->
    <section class="highlights">
      <h3>Principais Benefícios</h3>
      <div class="cards-grid">
        <div class="home-card" v-for="(card, index) in cards" :key="index">
          <i :class="card.iconClass"></i>
          <h4>{{ card.title }}</h4>
          <p>{{ card.description }}</p>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import ClockDisplay from '../components/ClockDisplay.vue'
export default {
  name: 'HomePage',
  components: { ClockDisplay },
  data() {
    return {
      cards: [
        {
          title: 'Interatividade',
          description: 'Interfaces dinâmicas e reativas com facilidade.',
          iconClass: 'fa-solid fa-bolt'
        },
        {
          title: 'Responsividade',
          description: 'Layout que se adapta a qualquer dispositivo.',
          iconClass: 'fa-solid fa-mobile-screen-button'
        },
        {
          title: 'Performance',
          description: 'Carregamento rápido e experiência suave.',
          iconClass: 'fa-solid fa-tachometer-alt'
        }
      ]
    }
  }
}
</script>

<style scoped>
/* ======== Carrossel ======== */
.carousel-container {
  position: relative;
  overflow: hidden;
  max-width: 1000px;
  height: 400px;
  margin: 0 auto 30px auto;
  border-radius: 6px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.3);
}
.carousel-slides {
  display: flex;
  animation: slideAnimation 12s infinite;
}
.carousel-slides img {
  width: 1000px;
  height: 400px;
  object-fit: cover;
  flex-shrink: 0;
  border-radius: 6px;
}
@keyframes slideAnimation {
  0%   { transform: translateX(0); }
  33%  { transform: translateX(-1000px); }
  66%  { transform: translateX(-2000px); }
  100% { transform: translateX(0); }
}

/* ======== Seção de destaque / texto principal ======== */
.welcome-text {
  text-align: center;
  margin-bottom: 30px;
}
.welcome-text h2 {
  margin-bottom: 10px;
}

/* ======== Destaques (cards) ======== */
.highlights {
  margin-top: 40px;
  text-align: center;
}
.cards-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
  max-width: 900px;
  margin: 20px auto;
}
.home-card {
  background: #fff;
  padding: 20px;
  border-radius: 6px;
  color: #333;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  text-align: center;
}
.home-card i {
  font-size: 2em;
  margin-bottom: 10px;
  color: #1f6aa5; /* cor do ícone */
}
</style>
