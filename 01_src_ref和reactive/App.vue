<template>
  <h1>你好</h1>
  <h2>姓名: {{name}}</h2>
  <h2>年龄: {{age}}</h2>
  <h2>工作: {{job.type}}</h2>
  <h2>工资: {{job.salary}}</h2>
  <h2>学校: {{school.name}}</h2>
  <h2>地址: {{school.address}}</h2>
  <button @click="change">ref修改信息</button>
  <button @click="change2">reactive修改信息</button>
</template>

<script>
import { ref, reactive } from 'vue'

export default {
  name: 'App',
  setup () {
    let name = ref('张三')
    let age = ref(20)
    let job = ref({
      type: '前端工程师',
      salary: '20k'
    })

    let school = reactive({
      name: '江财',
      address: '南昌'
    })


    function change () {
      name.value = '李四'
      age.value = 18
      job.value.type = 'java工程师'
      job.value.salary = '15k'
    }

    function change2 () {
      school.name = '上交大'
      school.address = '上海'
    }

    return {
      name,
      age,
      job,
      school,
      change,
      change2
    }
  }
}
</script>
<style>
</style>
