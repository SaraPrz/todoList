<template>
  <v-app id="app" >
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <Header />
    <Add @setTasks="setTasks" />
    <List :tasks="tasksList" />

  </v-app>
</template>

<script>
import Header from './components/Header.vue'
import List from './components/List.vue'
import Add from './components/Add.vue'

export default {
  name: 'App',
  components: {
    Header,
    List,
    Add
  },
  data() {
    return {
      tasksList : [
      ]
    }
  },
  methods : {
    setTasks(value , id) {
      this.tasksList.push({
        title : value,
        id : id,
        status: 'incomplete',
        completed: false
      });
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
