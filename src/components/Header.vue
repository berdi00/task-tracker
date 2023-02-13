<template>
  <header>
    <h1>{{ title }}</h1>
    <ButtonCp
      @toggle-add-task="$emit('toggle-add-task')"
      text="Add task"
      color="green"
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
