<template>
  <header class="header">
    <div class="header-left">
      <a href="#" class="site-title" @click.prevent="navigate('HomePage')">MY WEBSITE</a>
      <nav class="menu-links">
        <a
          href="#"
          :class="['menu-link', {active: activeView === 'HomePage'}]"
          @click.prevent="navigate('HomePage')"
        >Home</a>
        <a
          href="#"
          :class="['menu-link', {active: activeView === 'TodoPage'}]"
          @click.prevent="navigate('TodoPage')"
        >Tarefas</a>
        <a
          href="#"
          :class="['menu-link', {active: activeView === 'GalleryPage'}]"
          @click.prevent="navigate('GalleryPage')"
        >Galeria</a>
        <a
          href="#"
          :class="['menu-link', {active: activeView === 'ContactPage'}]"
          @click.prevent="navigate('ContactPage')"
        >Contato</a>
        <a
          href="#"
          :class="['menu-link', {active: activeView === 'AboutPage'}]"
          @click.prevent="navigate('AboutPage')"
        >Sobre</a>
      </nav>
    </div>
    <div class="header-right">
      <a href="#" class="profile-link" @click.prevent="navigate('Profile')">
        <i class="fa-solid fa-user"></i>
      </a>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    activeView: {
      type: String,
      default: 'HomePage'
    }
  },
  methods: {
    navigate(view) {
      this.$emit('navigate', view)
    }
  }
}
</script>

<style scoped>
.header {
  background-color: #1f6aa5;
  color: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  min-height: 100px;           /* Aumenta a altura do header */
  padding: 0 40px;             /* Aumenta o padding horizontal */
  box-sizing: border-box;
}

.header-left {
  display: flex;
  align-items: center;
}

.site-title {
  font-size: 2.5em;           /* Título maior */
  font-weight: bold;
  margin-right: 40px;
  color: #fff;
  text-decoration: none;
}

.menu-links {
  display: flex;
  gap: 40px;                  /* Espaçamento extra entre as opções */
}

.menu-link {
  font-size: 1.5em;           /* Aumenta o tamanho da fonte dos links */
  color: #fff;
  padding: 12px 16px;
  border-radius: 4px;
  text-decoration: none;
}

.menu-link:hover {
  background-color: #155d82;
  transition: background-color 0.3s;
}

.menu-link.active {
  background-color: #fff;
  color: #1f6aa5;
  font-weight: bold;
}

/* Garante espaçamento entre o menu e o ícone de perfil */
.header-right {
  margin-left: 40px;
}

.profile-link {
  font-size: 2em;           /* Ícone maior */
  color: #fff;
  padding: 12px;
  border-radius: 50%;
  transition: background-color 0.3s;
  text-decoration: none;
}

.profile-link:hover {
  background-color: rgba(255, 255, 255, 0.2);
}
</style>
