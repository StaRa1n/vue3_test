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

    //情况一: 检视ref所定义的单个响应式数据
    /* watch(sum, (newValue, oldValue) => {
      console.log('sum变了', newValue, oldValue);
    },{immediate: true}) */

    //情况二: 检视ref所定义的多个响应式数据
    /* watch([sum, msg], (newValue, oldValue) => {
      console.log('sum或msg变了', newValue, oldValue);
    }) */

    /* 情况三: 检视reactive所定义的单个响应式数据,
          *注意*: 1.无法获得正确的oldValue 
                  2.默认开启深度检视(无法配置deep)
    */
    /* watch(person, (newValue, oldValue) => {
      console.log('person变了', newValue, oldValue);
    }) */

    //情况四: 检视reactive所定义的单个响应式数据中的某一个数据
    /* watch(() => person.name, (oldValue, newValue) => {
      console.log('person中的name变化了', newValue, oldValue);
    }) */

    //情况四: 检视reactive所定义的单个响应式数据中的某些个数据
    /* watch([() => person.name, () => person.age], (oldValue, newValue) => {
      console.log('person中的name或age变化了', newValue, oldValue);
    }) */

    watch(person.job, (oldValue, newValue) => {
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