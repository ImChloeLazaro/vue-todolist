<script>
import RegisterUser from './components/RegisterUser.vue'
import TaskStatus from './components/TaskStatus.vue'
export default {
  data() {
    return {
      user: '',
      tasks: [{
        title: 'Task 1',
        done: false
      }, {
        title: 'Task 2',
        done: false
      }, {
        title: 'Task 3',
        done: false
      }],
      newTask: ''
    }
  },
  methods: {
    addTask() {
      this.tasks.push({
        title: this.newTask,
        done: false
      })
      this.newTask = ''
    },
    deleteTask(index) {
      this.tasks.splice(index, 1)
    },
    doneTask(index) {
      this.tasks[index].done = !this.tasks[index].done
    },
    registerUser(name) {
      this.user = name
    }
  },
  components: {
    RegisterUser,
    TaskStatus
  }
}
</script>
<template>
  <div v-if="!user">
    <RegisterUser @register="registerUser" />
  </div>
  <div v-else>
    <h1>Welcome, {{ user }}</h1>
    <h2>Tasks</h2>
    <TaskStatus :tasks="tasks"/>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <input type="checkbox" @change="doneTask(index)" :checked="task.done">
        <span :style="{textDecoration: task.done ? 'line-through' : 'none'}">{{ task.title }}</span>
        <button @click="deleteTask(index)">Delete</button>
      </li>
    </ul>
    <input type="text" v-model="newTask" placeholder="New Task">
    <button @click="addTask">Add Task</button>
  </div>
</template>
