<template>
  <h1>你好</h1>
  <!-- 传入props配置及自定义事件 -->
  <Student msg="props消息" msg2="props消息2" @hello="showHello">
    <!-- 具名插槽 -->
    <template v-slot:msg1>
      <span>插槽消息1</span>
    </template>

    <template v-slot:msg2>
      <span>插槽消息2</span>
    </template>

  </Student>
</template>

<script>
import Student from './components/Student.vue'

export default {
  components: { Student },
  name: 'App',
  setup () {
    function showHello (value) {
      console.log(`nihao${value}`);
    }

    return {
      showHello
    }
  }
}
</script>
<style>
</style>
