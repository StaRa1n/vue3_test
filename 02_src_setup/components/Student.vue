<template>
  <div>
    <h2>姓名: {{person.name}}</h2>
    <h2>年龄: {{person.age}}</h2>
    <slot name="msg1"></slot>
    <h2>接收: {{msg}}</h2>
    <slot name="msg2"></slot>
    <button @click="test">测试Hello方法</button>
  </div>
</template>

<script>
import { reactive } from 'vue';
export default {
  name: 'Vue3TestStudent',
  props: ['msg', 'msg2'],
  emits: ['hello'],
  setup (props, context) {
    console.log(props);
    console.log(context.slots);

    let person = reactive({
      name: '张三',
      age: 18
    })

    function test () {
      context.emit('hello', 'jiangcai')
    }

    return {
      person,
      test
    }
  }
};
</script>

<style lang="scss" scoped>
</style>