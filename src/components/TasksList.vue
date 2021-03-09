<template>
  <div class="task-list">
    <template v-if="tasks.length">
      <Task v-for="(task, i) in tasks" :key="task.name" 
      @taskDeleted="$emit('taskDeleted', i)"
      @taskStateChanged="$emit('taskStateChanged', i)"
      :task="task"></Task>
    </template>
    <p v-else class="no-task">Sua vida está em dia ;)</p>
  </div>
</template>

<script>
import Task from './Task.vue'

export default {
  components: { Task },

  props: {
    tasks: { type: Array, required: true}
  }
}
</script>

<style>
  .task-list {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
  }

  .no-task {
    color: #aaa;
    font-size: 1.7rem;
  }
</style>
