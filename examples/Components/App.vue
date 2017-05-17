<template>
  <div id="app">
    <h1>{{ header }}</h1>
    <p>Förälderns att göra lista</p>
    <ul>
      <li v-for="todo in todos">
        <h3>{{ todo.title }}</h3>
        <p>{{ todo.description }}</p>
      </li>
    </ul>

    <br><br>
    <hr>
    <br><br>

    <div class="child">TEST</div>

    <child name="Lars" v-on:sendTodo="addTodo" gender="male"></child>

    <child name="Elna" v-on:sendTodo="addTodo" gender="female"></child>

    <child name="Olov" v-on:sendTodo="addTodo" gender="male"></child>
  </div>
</template>

<script>
import Child from './components/child.vue'
export default {
  name: 'app',
  components: { Child },
  data () {
    return {
      header: 'Att göra',
      todos: []
    }
  },
  methods: {
    addTodo (title, description){
      this.todos.push({title: title, description: description})
    }
  }
}
</script>

<style>
</style>
