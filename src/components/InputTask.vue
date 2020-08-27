<template>
  <div class="InputTaskComponent">
    <form @submit.prevent="onSubmit">
    <h3>LIST TASK VUE DEMO</h3>
    <label >Enter Your Task: </label>

    <input id="task" v-model="taskInput">
    <input class="button" type="submit" value="submit">

  </form>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
      return {
        taskInput: '',
        taskStatus: false,
      }
    },
    methods: {
    onSubmit() {
      if (this.taskInput !== '') {
        let Task = {
          taskTitle: this.taskInput,
          taskActive: this.taskStatus,
        }
        this.$emit('task-submitted', Task)
        this.task = ''
      }
    }
  }
}


  
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
