<template>
  <div class="todo-page">
    <h2>Minha Lista de Tarefas</h2>
    <div class="task-input">
      <input type="text" v-model="newTask" placeholder="Adicionar nova tarefa" class="task-input-field" />
      <button class="pure-button pure-button-primary" @click="addTask">Adicionar</button>
    </div>
    <ul class="task-list">
      <li v-for="(task, index) in tasks" :key="index" class="task-item">
        <span :class="{ 'task-completed': task.completed }">{{ task.text }}</span>
        <div class="task-actions">
          <button class="pure-button" @click="toggleTask(index)">Toggle</button>
          <button class="pure-button pure-button-error" @click="removeTask(index)">Remover</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TodoPage',
  data() {
    return {
      newTask: '',
      tasks: JSON.parse(localStorage.getItem('tasks')) || []
    }
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({ text: this.newTask.trim(), completed: false })
        this.newTask = ''
        this.saveTasks()
      }
    },
    toggleTask(index) {
      this.tasks[index].completed = !this.tasks[index].completed
      this.saveTasks()
    },
    removeTask(index) {
      this.tasks.splice(index, 1)
      this.saveTasks()
    },
    saveTasks() {
      localStorage.setItem('tasks', JSON.stringify(this.tasks))
    }
  }
}
</script>

<style scoped>
.todo-page {
  max-width: 600px;
  margin: 0 auto;
}
h2 {
  text-align: center;
  margin-bottom: 20px;
}
.task-input {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}
.task-input-field {
  flex: 1;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}
.task-list {
  list-style: none;
  padding: 0;
}
.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border-bottom: 1px solid #eee;
}
.task-completed {
  text-decoration: line-through;
  color: #888;
}
.task-actions button {
  margin-left: 5px;
}
</style>
