<template>
    <label>Tasks (press alt + comma to add):</label>
    <input type="text" v-model="tempTask" @keyup.alt="addTask">
<li v-for="task in tasks" :key="task" @click="deleteTask(task)"> {{ task }} </li>
</template>

<script>

export default {
  name: 'App',
  data(){
  return{
    tempTask: "",
    tasks: []
  }
  },
  methods: {
    addTask($event) {
      if($event.key === ',' && this.tempTask) {
        if (!this.tasks.includes(this.tempTask)) {
          this.tasks.push(this.tempTask)
        }
        this.tempTask = ''
      }
    },
    deleteTask(task) {
      this.tasks = this.tasks.filter(item => {
        return task !== item
      })
    },
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
body{
  background: #eee;
  max-width: 960px;
  margin: 20px auto;
}
p, h3, ul{
  margin: 0;
  padding: 0;
}
li{
  list-style-type: none;
  background: #fff;
  margin: 20px auto;
  padding: 10px 20px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
