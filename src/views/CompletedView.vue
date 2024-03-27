<template>
  <div>
    <h2>Completed Tasks</h2>
    <div v-if="completedTasks.length > 0" class="scroll">
      <div
        v-for="(task, index) in completedTasks"
        :key="index"
        class="task-card"
      >
        <div class="card">
          <label :for="'completed-task-' + index" class="completed">{{
            task.title
          }}</label>
        </div>
      </div>
    </div>
    <p v-else>No completed tasks available.</p>
  </div>
</template>

<script>
export default {
  props: {
    tasks: {
      type: Array,
      required: true,
    },
  },
  computed: {
    completedTasks() {
      return this.tasks.filter((task) => task.completed);
    },
  },
};
</script>

<style scoped>
.task-card {
  margin-top: 1.5rem;
  display: flex;
  justify-content: center;
}

.card {
  width: 50%;
  height: auto;
  display: flex;
  align-items: center;
  padding: 10px;
  border: 1px solid hsla(160, 100%, 37%, 1);
  border-radius: 5px;
  justify-content: space-between;
}

.card label {
  flex-grow: 1;
  font-weight: 500;
  overflow-wrap: break-word;
}

.completed {
  text-decoration: line-through;
}

.scroll {
  margin-top: 1.5rem;
  height: 325px;
  overflow: scroll;
}

.scroll::-webkit-scrollbar {
  width: 0;
}

@media (max-width: 768px) {
  .card {
    width: auto;
  }

  .scroll {
    height: 200px;
  }
}
</style>
