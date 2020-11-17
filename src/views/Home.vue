<template>
  <div class="App">
    <h1>Todo App</h1>
    <p>{{ nbTodos }}</p>
    <ul class="todoList">
      <li
        class="elemList"
        v-for="(todo, index) in todos"
        :key="index"
        @click="removeTodo(index)"
      >
        {{ todo }}
      </li>
    </ul>
    <form @submit.prevent="handleSubmit()">
      <input v-model="inputValue" type="text" />
      <input type="submit" value="Envoyer" />
    </form>
    <br />
    <br />
    <br />
    <p>Event : @eventName="maFonction()"</p>
    <p>boucle in html : v-for="(todo, index) in todos"</p>
    <p>
      Lier une classe dynamiquement: :class="{ className: variableTrueOrFalse }"
    </p>
    <pre>
      Pour ajouter des variables accesssible au dom et réactive

      data() {
        return {
          todos: [],
          inputValue: '',
        };
      }
    </pre>
    <p>
      Pour créer une vriable dynamique / calculé
      <a href="https://fr.vuejs.org/v2/guide/computed.html">computed</a>
    </p>
    <p>
      Passer des variables aux enfants :
      <a href="https://fr.vuejs.org/v2/guide/components-props.html">Les props</a>
    </p>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';

export default {
  name: 'Home',
  data() {
    return {
      todos: [],
      inputValue: '',
    };
  },
  methods: {
    handleSubmit: function () {
      this.todos.push(this.inputValue);
      this.inputValue = '';
    },
    removeTodo: function (index) {
      this.todos.splice(index, 1);
    },
  },
  computed: {
    nbTodos: function () {
      return `IL y a ${this.todos.length} Todos`;
    },
  },
  components: {
    HelloWorld,
  },
};
</script>
<style lang="scss" scoped>
.App {
  margin: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  flex-direction: column;
  .todoList {
    list-style: none;
    .elemList:hover {
      cursor: pointer;
      text-decoration: line-through;
    }
  }
}
</style>
