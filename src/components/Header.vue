<template>
  <header>
    <h1>{{ title }}</h1>
    <ButtonCp
      @btn-click="$emit('btn-click')"
      :text="showAddTask ? 'Close' : 'Add Task' "
      :color="showAddTask ? 'red' : 'green'"
    />
  </header>
</template>

<script>
import ButtonCp from "./Button.vue";
export default {
  name: "HeaderComponent",
  components: {
    ButtonCp,
  },
  // props: ["title"],
  props: {
    title: String,
    showAddTask: Boolean
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
