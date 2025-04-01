<template>
  <div class="about-page">
    <h2>Sobre Este Projeto</h2>
    <p>
      Este projeto demonstra como integrar <strong>Vue.js</strong> e <strong>Pure.css</strong> para construir
      aplicações web modernas, dinâmicas e responsivas. A modularidade do Vue e a leveza do Pure.css
      tornam o desenvolvimento mais ágil e a experiência do usuário mais fluida.
    </p>
    <p><strong>Principais Recursos Implementados:</strong></p>
    <ul class="features-list">
      <li>Carrossel de imagens com CSS puro</li>
      <li>Lista de tarefas com persistência localStorage</li>
      <li>Formulário de contato com validação e feedback visual</li>
      <li>Navegação estilo SPA com transições suaves</li>
      <li>Galeria de imagens organizada em grid responsivo</li>
    </ul>
    <p>
      Sinta-se à vontade para tirar dúvidas! :)
    </p>
  </div>
</template>

<script>
export default {
  name: 'AboutPage'
}
</script>

<style scoped>
.about-page {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}
h2 {
  text-align: center;
  margin-bottom: 20px;
}
.features-list {
  list-style: disc inside;
  margin: 10px 0 20px 20px;
  line-height: 1.6;
}
</style>
