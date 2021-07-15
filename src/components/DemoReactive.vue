<template>
  <div>
    <div v-for="item in data1.todoList" :key="item.id">
      {{ item }}
    </div>
    <button type="button" @click="handleClick">
      count is: {{ data2.count }} double count is: {{ data2.double }}
    </button>
    <p>tempCount is {{ tempCount }}</p>
    <p>count is {{ count }}</p>
    <p>double is {{ double }}</p>
  </div>
</template>
<script setup lang="ts">
import { reactive, onMounted, computed, toRef, toRefs } from "vue";
type Todo = {
  id: number;
  message: string;
  completed: boolean;
  time: string;
};
type State = {
  count: number;
  double: number;
};
const data1 = reactive({
  todoList: [] as Todo[],
});
const data2: State = reactive({
  count: 0,
  double: computed(() => data2.count * 2),
});
const tempCount = toRef(data2, "count");
const { count, double } = toRefs(data2);
const handleClick = () => {
  data2.count++;
};
onMounted(() => {
  const todos: Todo[] = [
    {
      id: 1,
      message: "todo1",
      completed: true,
      time: "2021-7-15 07:00",
    },
    {
      id: 2,
      message: "todo2",
      completed: false,
      time: "2021-7-15 07:00",
    },
  ];
  data1.todoList = todos;
  data1.todoList.push({
    id: 3,
    message: "todo3",
    completed: true,
    time: "2021-7-15 07:00",
  });
});
</script>