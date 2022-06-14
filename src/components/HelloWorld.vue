<script setup>
import ClickCounter from "./ClickCounter.vue";
import ItemList from "./ItemList.vue";
import TodoList2 from "./TodoList2.vue";

defineProps({
  msg: { type: String, default: "" },
});
</script>

<template>
  <div>
    <h1>{{ msg }}</h1>
    <TodoList2 />
    <br />
    <br />
    <ClickCounter />
    <ItemList />
  </div>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
