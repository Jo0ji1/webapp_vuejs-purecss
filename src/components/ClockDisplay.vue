<template>
  <div class="clock-display">
    <h3>
      <i class="fa-solid fa-clock"></i>
      Relógio
    </h3>
    <p>{{ currentTime }}</p>
  </div>
</template>

<script>
export default {
  name: 'ClockDisplay',
  data() {
    return {
      currentTime: new Date().toLocaleTimeString()
    }
  },
  mounted() {
    setInterval(() => {
      this.currentTime = new Date().toLocaleTimeString()
    }, 1000)
  }
}
</script>

<style scoped>
.clock-display {
  margin-top: 20px;
  padding: 10px;
  background: #333; /* fundo escuro */
  border-radius: 5px;
  text-align: center;
  color: #fff;
  max-width: 200px; /* reduz a largura máxima */
  margin-left: auto;
  margin-right: auto; /* centraliza no container */
  box-shadow: 0 2px 5px rgba(0,0,0,0.3);
}
.clock-display h3 {
  margin: 0 0 5px 0;
  font-size: 1.1em;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
}
.clock-display p {
  margin: 0;
  font-size: 1.2em;
  font-weight: bold;
}
</style>
