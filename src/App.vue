<template>
  <div class="container">
    <Header title="Lista de Tarefas"/>
    <AddTask @add-task="addTask" />
    <Tasks @toggle-reminder="toggleReminder" 
    @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
  import Header from './components/Header'
  import Tasks from './components/Tasks'
  import AddTask from './components/AddTask'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [
        {
          id: 1,
          text: 'Doctors Appointment',
          day: 'March 1st at 2:30pm',
          reminder: true,
        },
        {
          id: 2,
          text: 'Meeting at School',
          day: 'March 3rd at 1:30pm',
          reminder: true,
        },
        {
          id: 3,
          text: 'Food Shopping',
          day: 'March 3rd at 11:00am',
          reminder: false,
        }
      ]
    }
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      if (confirm('Tem certeza que deseja remover essa tarefa?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id
      ? {...task, reminder: !task.reminder} : task) 
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.btn {
  display: inline-block;
  background: rgb(18, 131, 56);
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.container {
  width: 700px;
  height: auto;
  padding: 10px 20px;
  margin: 0 auto;
  border-radius: 20px;
  background: rgb(236, 192, 111);
}


</style>
