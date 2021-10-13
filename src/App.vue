<template>
  <div class="container">
     
    <Header @toggle-add-task="toggleTask" title="Task Tracker" />
    <div v-show="showAddTask" >
 <AddTask @add-task="addTask"/>
    </div>
  
    <Tasks
      @delete-task="deleteTask"
      @toggle-reminder="toggleReminder"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: [],
      showAddTask:false
    }
  },

  methods :{
    toggleTask (){
      this.showAddTask = !this.showAddTask
    },
    addTask(task){
      this.tasks = [...this.tasks,task]
    },
    deleteTask(id){
      this.tasks = this.tasks.filter((task)=>task.id !== id)
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task)=>task.id == id ? {...task, reminder: !task.reminder}:task)
    }
  },
  created() {
    this.tasks = [
      {
        id:1,
        text: "Booking",
        day : "1/1/11",
        reminder : true

      },
            {
        id:2,
        text: "Booking",
        day : "1/1/11",
        reminder : false

      },
            {
        id:3,
        text: "Booking",
        day : "1/1/11",
        reminder : true

      }
    ]
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
