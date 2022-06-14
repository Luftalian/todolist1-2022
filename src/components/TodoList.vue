<script setup>
import { ref } from "vue";

const items = ref([
  { task: "たまご買う", fine: "未完" },
  { task: "りんご買う", fine: "未完" },
]);
const newItemTask = ref("");
const newItemFine = ref(false);

const addItem = () => {
  if (newItemTask.value != "") {
    if (newItemFine.value == false) {
      items.value.push({
        task: newItemTask.value,
        fine: "未完",
      });
    } else {
      items.value.push({
        task: newItemTask.value,
        fine: "完了",
      });
    }
    newItemTask.value = "";
  }
};
const which = () => {
  if (newItemFine.value == false) {
    items.value.push({
      task: newItemTask.value,
      fine: "完了",
    });
    newItemFine.value == true;
  } else {
    items.value.push({
      task: newItemTask.value,
      fine: "未完",
    });
    newItemFine.value == false;
  }
  newItemTask.value = "";
};
/*
const allFine = () => {
  newItemFine.value = True;
};
const allNotFine = () => {
  newItemFine.value = True;
};
*/
</script>

<template>
  <div>
    <div>ItemList</div>

    <div id="tasklist">
      <div id="finished">
        <h1>完了</h1>
        <div v-for="item in items" :key="item.task">
          <div class="item" :class="{ finished: item.fine ==  }">
            <div class="task">タスク名: {{ item.task }}</div>
            <div class="fine">{{ item.fine }}</div>
            <button @click="which">完了</button>
          </div>
        </div>
      </div>
      <div id="unfinished">
        <h1>未完了</h1>
        <div v-for="item in items" :key="item.task">
          <div :id="{ finished: item.fine == true }">
            <div class="task">タスク名: {{ item.task }}</div>
            <div class="fine">{{ item.fine }}</div>
            <button @click="which">完了</button>
          </div>
        </div>
      </div>
    </div>

    <div>
      <label>
        タスク名
        <input v-model="newItemTask" type="text" />
      </label>
      <!--
      <label>
        完/未完
        <input v-model="newItemFine" type="bool" />
      </label>
      -->
      <button @click="addItem">add</button>
      <button @click="allFine">すべて完了</button>
      <button @click="allNotFine">すべて未完了</button>
    </div>
  </div>
</template>

<style>
.fine {
  /*display: none;*/
}
#tasklist {
  display: flex;
}
#finished {
  width: 50%;
  background-color: #0033ff7c;
}
#unfinished {
  width: 50%;
  background-color: #f600004a;
}
h1 {
  background-color: #ffffff;
}
</style>
