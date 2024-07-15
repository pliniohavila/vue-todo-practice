<script>
import TaskItem from './TaskItem.vue'

export default {
  name: 'TaskList',
  components: {
    TaskItem
  }, 
  data() {
    return {
      tasks: this.loadTasksFromStorage(),
    }
  }, 
  methods: {
    loadTasksFromStorage() {
      const tasks = JSON.parse(localStorage.getItem('task')) || []
      return tasks
    },
    
    syncTasksToStorage() {
      for (const task of this.tasks) {
        localStorage.setItem(task.id, JSON.stringify(task))
      }
    },
    handleStorageChange(event) {
      if (event.key && event.key.startsWith('task')) {
        this.tasks = this.loadTasksFromStorage()
      }
    },
  }, 
  mounted() {
    window.addEventListener('storage', this.handleStorageChange)
    console.log(this.tasks)
  }, 
  beforeUnmount() {
    window.removeEventListener('storage', this.handleStorageChange)
  },
}
</script>


<template>
  <div class="task-list d-flex flex-column gap-2 border border-secondary rounded p-2">
    <ul>
      <li v-for="(task) in tasks" :key="task.id">
        <TaskItem 
          :id="task.id" 
          :task="task.task" 
          :createdAt="task.createdAt" 
          :status="task.status" 
        />
      </li>
    </ul>
  </div>

</template>

<style scoped>
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
</style>
