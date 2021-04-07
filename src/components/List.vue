<template>
  <div>
    <ul>
      <li v-for="task in list" :key="task.index">
        <button @click="changeStatus(task.id)">
          {{ task.title }}
          {{ task.status }}
        </button> |
        <button @click="removeTask(task.id)">
          remove
        </button>
      </li>
    </ul>
      <div>
        تسک های ناتمام:
        {{incompleteTasks}}
      </div>
      <div>
        <button @click="removeCompleted">
        حذف تسک ها
      </button>
      </div>
  </div>
</template>

<script>

export default {
    data() {
      return {
        list : this.tasks
      }
    },
    props : {
      tasks: {
        type: Array
      },
    },
    methods: {
      changeStatus(id) {
        this.list.map(task => {
          if (task.id === id) {
            task.status = 'completed',
            task.completed = true
          }
        });
      },
      removeTask(id) {
        this.tasks.splice(id, 1);
      },
      removeCompleted() {
        this.list = this.list.filter(
          task => {
            task.status === 'incomplete'
          }
        );
      }
    },
    computed: {
      incompleteTasks(){
        const counter = this.list.map(
          task => {
            task.status === 'incomplete'
          }
        );
        return counter.length
      }

    }
  }


</script>

