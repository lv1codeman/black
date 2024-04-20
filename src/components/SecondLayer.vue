<script setup>
import { ref } from "vue";
const emit = defineEmits(["toPAPA", "toPAPA2"]);
emit("toPAPA", "msg from SecondLayer.vue");
emit("toPAPA2", "msg2 from SecondLayer.vue");

const name = ref("test name");
const setName = () => {
  name.value = "New name";
};

defineExpose({
  name,
  setName,
});
</script>
<template>
  <h3>This is SecondLayer.vue</h3>
  <div>{{ name }}</div>
</template>
<style scope>
.pend {
  padding-left: 20px;
}
</style>
