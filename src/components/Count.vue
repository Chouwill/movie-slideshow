<script setup>
import { ref } from "vue";

const counToal = ref(0);

const Onadd = () => {
  console.log("增加");
  counToal.value++;
};
const reduceNum = () => {
  console.log("減少");
    counToal.value--;

};
</script>

<template>
  <div class="Count-box">
    <h2>Count</h2>
    {{ counToal }}
    <button @click="Onadd">增加</button>
    <button @click="reduceNum">減少</button>
  </div>
</template>

<style lang="scss">
.Count-box {
  width: 100%;
  margin: 3rem 0;
}
</style>
