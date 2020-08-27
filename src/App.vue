<template>
  <div id="app">
    <InputTaskComponent  @task-submitted="addTaskMethod"/> 
    <DisplayTaskComponent @task-change-status="changeTextStatus" :taskListProp="taskListData"/> 
  </div>
</template>

<script>
import InputTaskComponent from './components/InputTask.vue'
import DisplayTaskComponent from './components/DisplayTask.vue'
import Vue from 'vue'

export default {
  name: 'App',
  data() {
      return {
        taskListData: []
      }
    },
  components: {
    InputTaskComponent,
    DisplayTaskComponent
  },
  methods: {
  addTaskMethod(text) {
    if (text !== '') {
      this.taskListData.push(text)
      console.log(this.taskListData)
    }
  },
  changeTextStatus(index) {
    const task = this.taskListData[index]
    Vue.$set(this.taskListData, index, {...task, taskActive: !task.taskActive})
  }
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
