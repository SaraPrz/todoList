<template>
<div>
  <v-text-field
      v-model="task"
      label="add task"
      placeholder="Add Task"
      outlined
      clearable
      :append-icon="'mdi-note-plus'"
      @click:append="addTasks"
    ></v-text-field>
</div>
</template>
<script>
export default {
  data(){
    return {
      task : '',
      tasks : []
    }
  },
  methods : {
    addTasks () {
      this.tasks.push(this.task);
      this.$emit('taskList' , this.tasks)
    }
  }
}
</script>