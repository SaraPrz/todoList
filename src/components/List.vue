<template>
  <div>
    <ul class="wrapper">
      <li v-for="task in list" :key="task.index" :class="{checked: task.completed}">
        <button @click="changeStatus(task.id)" >
          <span class="tasktitle">
            {{ task.title }}
          </span>
          <span class="taskstatus">
            ({{ task.status }})
          </span>
        </button>
        <button @click="removeTask(task.id)" class="close">
          <v-icon
          >
            mdi-delete
          </v-icon>
        </button>
      </li>
    </ul>
      <div class="incompletetasks">
        <span class="incomplete">
          تسک های ناتمام:
          {{incompleteTasks}}
        </span>
      </div>
      <div class="removetasks">
        <v-btn color="error">
          حذف تسک ها
        </v-btn>
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
        const counter = this.list.filter(
          task => 
            task.status === 'incomplete'
          
        );
        return counter.length;
      }

    }
  }
</script>
<style>
ul {
margin: 0;
padding: 0;
}
ul li {
  cursor: pointer;
  position: relative;
  padding: 12px 8px 12px 40px;
  list-style-type: none;
  background: #eee;
  font-size: 18px;
  transition: 0.2s;
  
  /* make the list items unselectable */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
ul li:nth-child(odd) {
  background: #f9f9f9;
}
.taskstatus {
  font-size: 12px;
  color: #f44336;
}
/* Darker background-color on hover */
ul li:hover {
  background: #ddd;
}
ul li.checked span.tasktitle{
  text-decoration: line-through;
}
ul li.checked .taskstatus {
  display: none;
}
/* Add a "checked" mark when clicked on */
ul li.checked::before {
  content: '';
  color: #38833c;
  position: absolute;
  border-style: solid;
  border-width: 0 2px 2px 0;
  top: 10px;
  left: 16px;
  transform: rotate(45deg);
  height: 15px;
  width: 7px;
}
/* Style the close button */
.close {
  position: absolute;
  right: 0;
  top: 0;
  padding: 12px 16px 12px 16px;
}
.close:hover {
  background-color: #f44336;
  color: #fff;
}
.incompletetasks {
  padding-top: 16px;
  width: 50%;
  float: right;
  
}
.incompletetasks .incomplete {
  padding: 8px;
  background-color: #489ceb;
  color: #fff;
  border-radius: 4px;
  margin-top: 16px;
}
.removetasks {
  margin-top: 8px;
  width: 50%;
  float: right;
}
</style>
