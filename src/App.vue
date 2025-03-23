<template>
  <div class="container">
    <h1>To-Do List</h1>

    <!-- Input untuk menambahkan tugas -->
    <input v-model="newTask" placeholder="Tambahkan tugas..." @keyup.enter="addTask" />
    <button @click="addTask">Tambah</button>

    <!-- Daftar tugas -->
    <ul>
      <TodoItem
        v-for="(task, index) in tasks"
        :key="index"
        :task="task"
        @remove="removeTask(index)"
      />
    </ul>
  </div>
</template>

<script>
import { ref } from 'vue';
import TodoItem from './components/Tugas.vue';

export default {
  components: { TodoItem },
  setup() {
    const newTask = ref('');
    const tasks = ref([]);

    const addTask = () => {
      if (newTask.value.trim() !== '') {
        tasks.value.push(newTask.value);
        newTask.value = '';
      }
    };

    const removeTask = (index) => {
      tasks.value.splice(index, 1);
    };

    return { newTask, tasks, addTask, removeTask };
  }
};
</script>

<style scoped>
.container {
  text-align: center;
  margin-top: 50px;
}
input {
  padding: 10px;
  margin-right: 10px;
}
button {
  padding: 10px;
  background-color: green;
  color: white;
  border: none;
  cursor: pointer;
}
ul {
  list-style: none;
  padding: 0;
}
</style>