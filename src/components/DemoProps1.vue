<template>
  <h1>{{ msg }}</h1>
  <button type="button" @click="count++">count is: {{ count }}</button>
</template>
/**  有问题
<script setup="props" lang="ts">
import { ref, toRefs, defineComponent } from "vue";
const { msg } = toRefs(props)
const count = ref(0);
</script>
*/

<script lang="ts">
import { ref, toRefs, defineComponent } from "vue";
// 这样写就没问题，很奇怪
export default defineComponent( {
  props: {
    msg: String
  },
  setup(props: any) { // 这应该是(props: Props) 但是这个Props找不到引用的地方，就写了any
    const {msg} = toRefs(props);
    
    const count = ref(0);
    return {msg, count}
  },
});
</script>


<style scoped>
</style>
