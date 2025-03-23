<template>
    <li class="todo-item">
      {{ task }}
      <button @click="$emit('remove')">Hapus</button>
    </li>
  </template>
  
  <script>
  export default {
    props: {
      task: String
    }
  };
  </script>
  
  <style scoped>
  .todo-item {
    background: #f4f4f4;
    padding: 10px;
    margin: 5px;
    display: flex;
    justify-content: space-between;
    border-radius: 5px;
  }
  button {
    background-color: red;
    color: white;
    border: none;
    cursor: pointer;
  }
  </style>