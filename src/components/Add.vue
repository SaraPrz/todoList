<template>
<div class="wrapper">
  <v-text-field
      v-model="task"
      @keyup.enter="addTasks"
      label="add task"
      placeholder="تسک"
      outlined
      clearable
      class="add"
    ></v-text-field>
  <v-btn
    class="green white--text text-center addtasks"
    x-large
    color="red darken-3"
    @click="addTasks"
  >
    افزودن تسک
  </v-btn>
 
</div>
</template>
<script>
import { v4 as uuidv4 } from 'uuid';
export default {
  data(){
    return {
      task : '',
      tasks : []
    }
  },
  methods : {
    addTasks () {
      this.$emit('setTasks' , this.task, uuidv4());
      this.task = ''
    }
  }
}
</script>
<style>
@import "../../node_modules/font-awesome/css/font-awesome.css";
@import "../../node_modules/@aasaam/noto-font/dist/font-face.css";
  * {
    font-family: 'aasaam-Noto';
  }
  .wrapper {
    width: 100%;
    max-width: 1200px;
    display: table;
    margin: 0 auto;;
  }
  .add {
    width: 80%;
    float: right;
  }
  .addtasks {
    width: 20%;
    float: right;
    padding: 15px 0;
  }
</style>