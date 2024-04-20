<script setup>
defineProps({
  msg1: String,
  msg2: String,
  arrMsg: Array,
  objMsg: Object,
});
// 或是
// const props = defineProps(["msg1", "msg2", "arrMsg", "objMsg"]);

const emit = defineEmits(["toPAPA"]);
emit("toPAPA", "msg from SecondLayer.vue");
</script>
<template>
  <h3>This is SecondLayer.vue</h3>
  <h3>父組件傳過來的資料</h3>
  <div>msg1 from app.vue: {{ msg1 }}</div>
  <div>msg2 from app.vue: {{ msg2 }}</div>
  <div>The name of first element in arrMsg: {{ arrMsg[0].name }}</div>
  arrMsg:
  <div v-for="item in arrMsg" :key="item.id">
    &nbsp;&nbsp;{{ item.id }}-{{ item.name }}
  </div>
  <div>object1.name = {{ objMsg.name }}</div>
  <div>object1.age = {{ objMsg.age }}</div>
  <div>object1.gender = {{ objMsg.gender }}</div>
</template>

<style scope>
.pend {
  padding-left: 20px;
}
</style>
