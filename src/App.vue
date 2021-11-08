<template>
  <div id="app" class="container">
    <input type="text" v-model="message" />
    <button v-on:click="add(message)">Submit</button>

    <br /><br />

    <ul v-for="(todo, i) in todos" :key="i">
      <li>
        {{ todo.message }}
        <a href="#" v-on:click="remove(todo.id)">x</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: '',
      todos: [
        // { id: 1, message: '1' },
        // { id: 2, message: '2' },
        // { id: 3, message: '3' },
        // { id: 4, message: '4' },
        // { id: 5, message: '5' },
      ],
    };
  },

  methods: {
    add(message) {
      const newMessage = {
        id: new Date().toISOString(),
        message: message,
      };
      this.todos.push(newMessage);
      this.message = '';
    },

    remove(removeId) {
      const removeIndex = this.todos.findIndex((todo) => todo.id === removeId);
      this.todos.splice(removeIndex, 1);
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
}

a {
  text-decoration: none;
  color: red;
}
</style>
