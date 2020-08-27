<template>
  <div class="DisplayTaskComponent">
    <ul id="TaskList">
      <li
        @click="onChangeStatus(taskIndex)"
        v-bind:class="{'line-through': task.taskActive }"
        v-for="(task, taskIndex) in taskListProp"
        :key="task.taskTitle"
      >{{ task.taskTitle }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["taskListProp"],
  methods: {
    onChangeStatus(index) {
      this.$emit("task-change-status", index);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.line-through {
  text-decoration: line-through;
}
</style>
