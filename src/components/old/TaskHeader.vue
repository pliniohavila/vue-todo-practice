<script setup>
// import TaskNew from './TaskNew.vue'
// import TaskNew from './TaskNew.vue'

defineProps({
  msg: {
    type: String,
    required: true
  }
})

</script>

<template>
  <div class="header-title">
    <h1 class="green">{{ msg }}</h1>
  </div>
  <!-- <TaskNew /> -->

  <!-- <div class="filters w-10 mt-3">
    <h3>Filters</h3>
    <div class="input-group row">
      <div class="w-100 d-flex flex-row gap-2 mb-3">
        <div class="col-8 ml-1">
          <input type="text" class="form-control" id="search" placeholder="Search Task">
        </div>
        <div class="col-4 d-flex gap-2 "> 
          <button type="button" class="btn btn-outline-primary ml-1">Completed</button>
          <button type="button" class="btn btn-outline-warning">Pending</button>
        </div>
      </div>
    </div>
  </div>
</template> -->

<style scoped>

h1 {
  text-align: center;
  font-weight: 500;
  font-size: 2.6rem;
  color: var(--color-secondary);
}

.filters {
  margin-top: 1rem;
  width: 100%;
}

</style>
