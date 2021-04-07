<template>
<div>
  <v-text-field
      v-model="task"
      @keyup.enter="addTasks"
      label="add task"
      placeholder="Add Task"
      outlined
      clearable
    ></v-text-field>
  <button @click="addTasks">افزودن تسک</button>
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
      // this.tasks.push(this.task);
      this.$emit('setTasks' , this.task, uuidv4());
      this.task = ''
    }
  }
}
</script>