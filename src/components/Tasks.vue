<template>
  <div :key="task.id" v-for="task in tasks">
    <TaskCp
      @toggle-reminder="$emit('toggle-reminder', task.id)"
      @delete-task="$emit('delete-task', task.id)"
      :task="task"
    />
  </div>
</template>

<script>
import TaskCp from "@/components/Task.vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "TasksCp",
  props: {
    tasks: Array,
  },
  components: {
    TaskCp,
  },

  emits: ["delete-task", "toggle-reminder"],
});
</script>
