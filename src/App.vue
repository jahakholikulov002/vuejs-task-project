<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Notes" :showAddTask="showAddTask" />
    <div v-if="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>

</template>
<script>
import Header from '@/components/Header';
import Tasks from '@/components/Tasks';
import AddTask from '@/components/AddTask'
export default { // component larni export import qiliw uchun 
  name: "App", // ismini registratsiya qlib olamiz 
  components: { // registratsiyadan utagn componentlar 
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false
    }
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      if (confirm('Are you sure to delete?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? { ...task, reminder: !task.reminder } : task)

    }
  },
  created() {
    this.tasks = [  //  Bu yerda biz qullayotgan "this." methodi bizning data ga teng
      {
        id: 1,
        text: 'Liverpool was created',
        day: 'March 1st march 1989 at 2:30pm',
        reminder: true
      },
      {
        id: 2,
        text: 'Barcelona was created',
        day: 'January 1st march 1989 at 1:30pm',
        reminder: true
      },
      {
        id: 3,
        text: 'Chelsea was created',
        day: 'March 1st march 1919 at 2:30pm',
        reminder: false
      },

    ]
  }
}

</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Poppins:ital,wght@0,600;0,700;1,400;1,500&display=swap');

* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

body {
  font-family: "Poppins", sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
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

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
