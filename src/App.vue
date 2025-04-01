<template>
  <div class="app-container">
    <Header @navigate="changeView" :activeView="currentView" />
    <main class="content">
      <transition name="fade" mode="out-in">
        <component :is="currentView" />
      </transition>
    </main>
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

// Import das páginas existentes
import HomePage from './pages/HomePage.vue'
import TodoPage from './pages/TodoPage.vue'
import GalleryPage from './pages/GalleryPage.vue'
import ContactPage from './pages/ContactPage.vue'
import AboutPage from './pages/AboutPage.vue'
import Profile from './pages/Profile.vue'

export default {
  name: 'App',
  data() {
    return {
      currentView: 'HomePage'
    }
  },
  components: {
    Header,
    Footer,
    HomePage,
    TodoPage,
    GalleryPage,
    ContactPage,
    AboutPage,
    Profile
  },
  methods: {
    changeView(view) {
      this.currentView = view
    }
  }
}
</script>

<style scoped>
.app-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
.content {
  flex: 1;
  margin: 80px 20px;
}

/* Transição fade */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
