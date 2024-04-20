<script setup>
import { ref } from "vue";
import SecondLayer from "./components/SecondLayer.vue";

const msg = ref("msg2 to child component.");
const array1 = [
  { id: 1, name: "Kiangkiang" },
  { id: 2, name: "Xiaohong" },
  { id: 3, name: "Xiaoma" },
];
const object1 = {
  name: "Xiaoma",
  age: "18",
  gender: "Boy",
};
//接收子組件傳來的資料
const dataFromSon = ref("");
const fromSon = (data) => {
  dataFromSon.value = data;
  console.log(dataFromSon.value);
};
</script>
<template>
  <h3>This is App.vue</h3>
  <div>子組件傳過來的資料: {{ dataFromSon }}</div>
  <hr />
  <h3>傳給子組件的資料</h3>
  <input v-model="msg" placeholder="key something" />
  <div>msg: {{ msg }}</div>
  <div class="pend">
    <SecondLayer
      msg1="msg1 to child component."
      :msg2="msg"
      :arrMsg="array1"
      :objMsg="object1"
      @toPAPA="fromSon"
    >
    </SecondLayer>
  </div>
</template>

<style scope>
.pend {
  padding-left: 20px;
}
</style>
