<template>
  <div>
    <!-- Task counter -->
    <div class="counter">
      <p>Total Tasks: {{ totalTasks }}</p>
      <p>Completed Tasks: {{ completedTasks }}</p>
    </div>

    <!-- Task input form also @submit.prevent preven the page to open new page. -->
    <form @submit.prevent="addTask">
      <input
        type="text"
        v-model="newTask"
        placeholder="Input new task here"
        required
      />
      <button type="submit">Add Task</button>
    </form>

    <!-- Display tasks -->
    <div class="scroll">
      <div v-if="tasks.length > 0">
        <div v-for="(task, index) in tasks" :key="index" class="task-card">
          <div class="card">
            <input
              type="checkbox"
              :id="'task-' + index"
              v-model="task.completed"
              @change="updateTask(index)"
            />

            <!-- this part is will show when the user click on the update button for each card it enable the user to update title name. -->
            <input
              type="text"
              v-model="task.title"
              v-if="editingIndex === index"
            />
            <!-- display task/title for each card -->
            <label
              v-else
              :for="'task-' + index"
              :class="{ completed: task.completed }"
              >{{ task.title }}</label
            >

            <!-- controls for updating or removing task. -->
            <div class="button-container">
              <button @click="removeTask(index)">Remove</button>
              <button
                @click="
                  editingIndex === index ? saveTask(index) : editTask(index)
                "
              >
                {{ editingIndex === index ? "Save" : "Update" }}
              </button>
            </div>
          </div>
        </div>
      </div>
      <!-- default display if there`s no available task shown. -->
      <p id="no-task" v-else>No tasks available.</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [],
      newTask: "",
      editingIndex: null,
      editedTask: "",
    };
  },
  computed: {
    // counter for total and completed task as the name suggest it display total task and completed task.
    totalTasks() {
      return this.tasks.length;
    },
    completedTasks() {
      return this.tasks.filter((task) => task.completed).length;
    },
  },
  mounted() {
    // Load tasks from local storage when the component is mounted
    const storedTasks = localStorage.getItem("tasks");
    if (storedTasks) {
      this.tasks = JSON.parse(storedTasks);
    }
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== "") {
        this.tasks.push({ title: this.newTask.trim(), completed: false });
        this.newTask = "";
        this.saveTasksToLocalStorage();
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
      this.saveTasksToLocalStorage();
    },
    updateTask(index) {
      this.saveTasksToLocalStorage();
    },
    editTask(index) {
      this.editingIndex = index;
      // Store the original task title
      this.editedTask = this.tasks[index].title;
    },
    saveTask(index) {
      // Revert to original title if new title is empty
      if (this.tasks[index].title.trim() === "") {
        this.tasks[index].title = this.editedTask;
      }
      this.editingIndex = null;
      this.editedTask = "";
      this.saveTasksToLocalStorage();
    },
    saveTasksToLocalStorage() {
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
    },
  },
};
</script>

<style scoped>
.counter {
  margin: 10px;
  display: flex;
  justify-content: center;
}

.counter p {
  padding: 10px;
  width: 200px;
  margin-left: 5px;
  border-radius: 5px;
  text-align: center;
  font-weight: bolder;
  color: #181818;
  background-color: hsla(160, 100%, 37%, 1);
}

.scroll {
  margin-top: 1.5rem;
  height: 325px;
  overflow: scroll;
}

.scroll::-webkit-scrollbar {
  width: 0;
}

.task-card {
  margin-top: 1.5rem;
  display: flex;
  justify-content: center; /* Center the cards horizontally */
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

.card input[type="checkbox"] {
  padding: 10px;
  margin-right: 10px;
}

.card label {
  flex-grow: 1; /* To allow the label to take up remaining space */
  font-weight: 500;
  max-width: calc(100% - 200px); /* Adjust the max-width as needed */
  overflow-wrap: break-word; /* Allow long words to wrap */
}

.button-container {
  margin-top: -10px;
  display: flex;
}

.button-container button {
  margin-left: 5px; /* Add space between buttons */
}

#no-task {
  margin-top: 2rem;
  text-align: center;
}

.completed {
  text-decoration: line-through;
}

@media (max-width: 1920px) {
  .scroll {
    height: 500px;
  }
}

@media (max-width: 1440px) {
  .scroll {
    height: 325px;
  }
}

@media (max-width: 1200px) {
  .scroll {
    height: 300px;
  }
}

@media (max-width: 768px) {
  .card {
    width: auto;
  }

  .card label {
    margin-right: 10px;
    max-width: calc(100% - 20px); /* Adjust the max-width as needed */
    overflow-wrap: break-word; /* Allow long words to wrap */
  }

  .button-container {
    margin-top: -10px;
    display: block;
  }

  .button-container button {
    width: 80px;
    font-size: 10px;
    margin-left: 5px; /* Add space between buttons */
  }

  .scroll {
    height: 200px;
  }
}
</style>
