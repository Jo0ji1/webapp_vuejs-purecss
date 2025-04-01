<template>
  <div class="contact-page">
    <h2>Fale Conosco</h2>
    <form class="contact-form" @submit.prevent="submitForm">
      <fieldset>
        <label for="name">Nome</label>
        <input
          id="name"
          type="text"
          v-model="name"
          :class="{'input-error': errors.name}"
          required
        />
        <small v-if="errors.name" class="error-msg">{{ errors.name }}</small>

        <label for="email">Email</label>
        <input
          id="email"
          type="email"
          v-model="email"
          :class="{'input-error': errors.email}"
          required
        />
        <small v-if="errors.email" class="error-msg">{{ errors.email }}</small>

        <label for="message">Mensagem</label>
        <textarea
          id="message"
          v-model="message"
          :class="{'input-error': errors.message}"
          required
        ></textarea>
        <small v-if="errors.message" class="error-msg">{{ errors.message }}</small>

        <button type="submit" class="pure-button pure-button-primary">Enviar</button>
      </fieldset>
    </form>
    <div v-if="submitted" class="success-message">
      <h3>Obrigado, {{ name }}!</h3>
      <p>Sua mensagem foi enviada com sucesso.</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ContactPage',
  data() {
    return {
      name: '',
      email: '',
      message: '',
      errors: {},
      submitted: false
    }
  },
  methods: {
    validateForm() {
      this.errors = {}
      let valid = true
      if (!this.name.trim()) {
        this.errors.name = 'O nome é obrigatório.'
        valid = false
      }
      if (!this.email.trim() || !this.email.includes('@')) {
        this.errors.email = 'Digite um email válido.'
        valid = false
      }
      if (!this.message.trim()) {
        this.errors.message = 'A mensagem não pode ficar em branco.'
        valid = false
      }
      return valid
    },
    submitForm() {
      if (this.validateForm()) {
        this.submitted = true
      }
    }
  }
}
</script>

<style scoped>
.contact-page {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  color: #fff; /* se o fundo do site for escuro */
}
h2 {
  text-align: center;
  margin-bottom: 20px;
}
.contact-form fieldset {
  border: none;
  padding: 0;
}
.contact-form label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}
.contact-form input,
.contact-form textarea {
  width: 100%;
  padding: 8px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  background-color: #333; /* se quiser um fundo escuro para o input */
  color: #fff; /* texto branco */
}
.input-error {
  border-color: #d9534f;
}
.error-msg {
  color: #d9534f;
  font-size: 0.9em;
  margin-bottom: 10px;
  display: block;
}
.success-message {
  background: #dff0d8;
  border: 1px solid #d0e9c6;
  padding: 15px;
  margin-top: 20px;
  border-radius: 4px;
  text-align: center;
  color: #155d82;
}
</style>
