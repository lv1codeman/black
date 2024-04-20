<script setup>
import { onMounted, ref } from "vue";
import SecondLayer from "./components/SecondLayer.vue";

//接收子組件傳來的資料
const dataFromSon = ref("");
const dataFromSon2 = ref("");
const fromSon = (data) => {
  dataFromSon.value = data;
  console.log(dataFromSon.value);
};
const fromSon2 = (data) => {
  dataFromSon2.value = data;
  console.log(dataFromSon2.value);
};

const childRef = ref(null);
const showChildName = ref(null);

// <SecondLayer ref="childRef"></SecondLayer>
// ref="childRef"為模板引用，需在onMounted()掛載完畢以後才會生效，如果沒有寫在onMounted()中，那就是還在setup的時候，也就是beforeCreate和created之後，此時還沒有mount所以模板引用無法生效
onMounted(() => {
  console.log(childRef.value);
  //調用子組件的setName()修改name
  childRef.value.setName();
  //因為被setName()修改name所以結果為"New name"
  showChildName.value = childRef.value.name;
});
</script>
<template>
  <h3>This is App.vue</h3>
  <div>子組件傳過來的資料1: {{ dataFromSon }}</div>
  <div>子組件傳過來的資料2: {{ showChildName }}</div>
  <div>子組件的name: {{ dataFromSon2 }}</div>
  <hr />
  <div class="pend">
    <SecondLayer @toPAPA="fromSon" @toPAPA2="fromSon2" ref="childRef">
    </SecondLayer>
  </div>
</template>

<style scope>
.pend {
  padding-left: 20px;
}
</style>
