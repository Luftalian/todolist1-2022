<script setup>
import { ref } from "vue";

const items = ref([
  { name: "たまご", price: 0 },
  { name: "りんご", price: 0 },
]);
const newItemName = ref("");
const newItemPrice = ref(0);

const addItem = () => {
  if (newItemName.value != "") {
    items.value.push({ name: newItemName.value, price: newItemPrice.value });
    newItemName.value = "";
    newItemPrice.value = 0;
  }
};
const finish = () => {
  if (newItemPrice.value == 0) {
    newItemPrice.value = 1;
    newItemName.value = getElementsByClassName("name");

    items.value.push({ name: newItemName.value, price: newItemPrice.value });
  } else {
    newItemPrice.value = 0;
    newItemName.value = "item.name";
    items.value.push({ name: newItemName.value, price: newItemPrice.value });
  }
};
</script>

<template>
  <div>
    <div>ItemList</div>
    <div v-for="item in items" :key="item.name">
      <!--<div class="item" :class="{ over500: item.price >= 500 }">-->
      <div class="name">名前: {{ item.name }}</div>
      <div class="price">{{ item.price }} 円</div>
      <button @click="finish">add</button>
    </div>
  </div>
  <div>
    <label>
      名前
      <input v-model="newItemName" type="text" />
    </label>
    <button @click="addItem">add</button>
  </div>
  <!--</div>-->
</template>

<style>
.over500 {
  color: red;
}
</style>
