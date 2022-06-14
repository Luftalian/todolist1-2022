<script setup>
import { ref } from "vue";

const items = ref([
  { name: "たまご", price: 100 },
  { name: "りんご", price: 160 },
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
</script>

<template>
  <div>
    <div>ItemList</div>
    <div v-for="item in items" :key="item.name">
      <div class="item" :class="{ over500: item.price >= 500 }">
        <div class="name">名前: {{ item.name }}</div>
        <div class="price">{{ item.price }} 円</div>
      </div>
    </div>
    <div>
      <label>
        名前
        <input v-model="newItemName" type="text" />
      </label>
      <label>
        価格
        <input v-model="newItemPrice" type="number" />
      </label>
      <button @click="addItem">add</button>
    </div>
  </div>
</template>

<style>
.over500 {
  color: red;
}
</style>
