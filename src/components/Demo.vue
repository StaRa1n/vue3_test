<template>
  <div>
    <h2>当前求和为: {{sum}}</h2>
    <button @click="sum++">点我num+1</button>
    <h2>当前信息为: {{msg}}</h2>
    <button @click="msg+='!'">点我msg+!</button>
    <hr>
    <h2>姓名: {{person.name}}</h2>
    <h2>年龄: {{person.age}}</h2>
    <h2>工资: {{person.job.j1.salary}}</h2>
    <button @click="person.name += '6'">修改姓名</button>
    <button @click="person.age ++">修改年龄</button>
    <button @click="person.job.j1.salary ++">修改薪资</button>
  </div>
</template>

<script>
import { ref, reactive, watch } from 'vue';
export default {
  name: 'Vue3TestStudent',
  setup () {
    let sum = ref(0)
    let msg = ref('你好')
    let person = reactive({
      name: '张三',
      age: 18,
      job: {
        j1: {
          salary: 20
        }
      }
    })

    watch(person, (oldValue, newValue) => {
      console.log('person中的job变化了', newValue, oldValue);
    })

    return {
      sum,
      msg,
      person
    }
  }
};
</script>

<style lang="scss" scoped>
</style>