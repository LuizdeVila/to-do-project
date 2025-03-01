<template>
  <div>
    <v-text-field
      clearable
      label="Add Task"
      :rules="rules"
      v-model="taskStore.titleTaskCreating"
      @keyup.enter="taskStore.addTask"
    ></v-text-field>

    <ListTasks />
  </div>
</template>

<script setup>
import { onMounted } from "vue"
import { useTaskStore } from "@/store/task"
import ListTasks from "./ListTasks.vue"

const taskStore = useTaskStore()

const rules = [
  (value) => {
    if (!value || value.length >= 5) return true
    return "You must enter Task title with more than 5 characters."
  },
]

onMounted(() => {
  taskStore.getTasks()
})
</script>