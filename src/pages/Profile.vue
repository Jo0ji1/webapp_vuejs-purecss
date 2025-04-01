<template>
  <div class="profile-page">
    <div v-if="!loggedIn" class="login-container">
      <h2>Login</h2>
      <form @submit.prevent="login">
        <label for="username">Usuário</label>
        <input id="username" v-model="username" type="text" placeholder="Digite seu usuário" required />
        <label for="password">Senha</label>
        <input id="password" v-model="password" type="password" placeholder="Digite sua senha" required />
        <button type="submit">Entrar</button>
      </form>
    </div>
    <div v-else class="dashboard">
      <h2>Bem-vindo, {{ username }}!</h2>
      <p>Aqui está sua galeria personalizada:</p>
      <div class="dashboard-gallery">
        <div class="gallery-card" v-for="(image, index) in userGallery" :key="index">
          <img :src="image" alt="Usuário" />
          <button @click="removeImage(index)">Remover</button>
        </div>
      </div>
      <div class="add-image">
        <h3>Adicionar nova imagem</h3>
        <input type="text" v-model="newImage" placeholder="URL da imagem" />
        <button @click="addImage">Adicionar</button>
      </div>
      <button class="logout" @click="logout">Sair</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Profile',
  data() {
    return {
      loggedIn: false,
      username: '',
      password: '',
      userGallery: [],
      newImage: ''
    }
  },
  methods: {
    login() {
      // Simulação simples de login
      if (this.username && this.password) {
        this.loggedIn = true;
        const gallery = localStorage.getItem(`gallery_${this.username}`);
        this.userGallery = gallery ? JSON.parse(gallery) : [];
      }
    },
    logout() {
      this.loggedIn = false;
      this.username = '';
      this.password = '';
      this.userGallery = [];
      this.newImage = '';
    },
    addImage() {
      if (this.newImage.trim()) {
        this.userGallery.push(this.newImage.trim());
        this.newImage = '';
        this.saveGallery();
      }
    },
    removeImage(index) {
      this.userGallery.splice(index, 1);
      this.saveGallery();
    },
    saveGallery() {
      localStorage.setItem(`gallery_${this.username}`, JSON.stringify(this.userGallery));
    }
  }
}
</script>

<style scoped>
.profile-page {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}
.login-container, .dashboard {
  background: #fff;
  padding: 20px;
  border-radius: 6px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  color: #333;
}
.login-container h2, .dashboard h2 {
  text-align: center;
}
.login-container form {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.login-container input {
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}
.dashboard-gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 15px;
  margin: 20px 0;
}
.gallery-card {
  background: #f9f9f9;
  border: 1px solid #ddd;
  border-radius: 4px;
  padding: 10px;
  text-align: center;
}
.gallery-card img {
  max-width: 100%;
  border-radius: 4px;
  margin-bottom: 5px;
}
.add-image {
  margin: 20px 0;
  display: flex;
  align-items: center;
  gap: 10px;
}
.add-image input {
  flex: 1;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}
.add-image button {
  padding: 8px 12px;
  border: none;
  background: #1f6aa5;
  color: #fff;
  border-radius: 4px;
}
.logout {
  display: block;
  margin: 20px auto 0;
  padding: 10px 20px;
  background: #d9534f;
  color: #fff;
  border: none;
  border-radius: 4px;
}
</style>
