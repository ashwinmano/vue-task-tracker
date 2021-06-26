<template>
  <div class="container">
    <Header @toggle-add-click="toggleAddClick" title="Task Tracker" :showAddTask="showAddTask" />
    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks @toggle-remainder="toggleRemainder" :tasks="tasks" @deleteTask="deleteTask" />
    
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'


export default {
  name:'App',
  components:{
    Header,
    Tasks,
    AddTask
  },
  data(){
    return{
      tasks:[],
      showAddTask:false
    }
  },
  methods:{

    toggleAddClick(){
      this.showAddTask=!this.showAddTask
    },
    deleteTask(id){
      if(confirm('Are you sure')){
        this.tasks = this.tasks.filter((task) =>task.id !== id)
      }
    },

    toggleRemainder(id){
      this.tasks=this.tasks.map((task) =>task.id === id?{...task,remainder:!task.remainder}:task)
    },

    addTask(task){
      this.tasks=[...this.tasks,task]
    },

  },
  created(){
    this.tasks=[
      {
        id:1,
        text:'Doctors Appointment',
        day:'april 1 at 12.30 PM',
        remainder:true
      },
      {
        id:2,
        text:'Teachers Appointment',
        day:'march 1 at 12.30 PM',
        remainder:false
      },
      {
        id:3,
        text:'Kitchen Appointment',
        day:'december 1 at 12.30 PM',
        remainder:true
      }
    ]
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body{
    font-family: 'Poppins',sans-serif;
}

.container{
    width: 500px;
    border: 1px solid steelblue;
    margin: 30px auto;
    min-height: 300px;
    padding: 30px;
    overflow: auto;
    border-radius: 5px;
}

.btn{
  display: inline-block;
  background-color: #000;
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus{
  outline: none;
}

.btn:active{
  transform: (0.98);
}

.btn-block{
  display: block;
  width: 100%;
}

</style>
