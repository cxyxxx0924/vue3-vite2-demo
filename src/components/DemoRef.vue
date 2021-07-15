<template>
  <h1>{{ msg }}</h1>
  <p>{{ state.msg }}</p>
  <div v-for="item in list" :key="item.msg">
    {{ item.msg }}
  </div>
  <button type="button" @click="handleClick">count is: {{ count }}</button>
</template>
<script setup lang="ts">
import { ref, defineProps } from "vue";
type Props = {
  msg: String;
};
defineProps<Props>();
const count = ref(0);
const state = ref<Props>({ msg: "123" });
const list = ref<Props[]>();
console.log(count.value);
console.log(count);
list.value = [
  { msg: "item 1" },
  { msg: "item 2" },
  { msg: "item 3" },
  { msg: "item 4" },
];
const handleClick = () => {
  count.value++;
};
</script>