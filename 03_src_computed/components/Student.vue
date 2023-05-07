<template>
  <div>
    姓: <input type="text" v-model="person.firstName"><br>
    名: <input type="text" v-model="person.lastName"><br>
    {{person.fullName}}
  </div>
</template>

<script>
import { reactive, computed } from 'vue';
export default {
  name: 'Vue3TestStudent',
  setup () {
    const person = reactive({
      firstName: '张',
      lastName: '三',
    })

    // 简写 (计算属性没有考虑被修改)
    /* person.fullName = computed(() => {
      return person.firstName + '-' + person.lastName
    }) */

    //完整
    person.fullName = computed({
      get () {
        return person.firstName + '-' + person.lastName
      },
      set (value) {
        const nameArr = value.split('-')
        person.firstName = nameArr[0]
        person.firstName = nameArr[1]
      }
    })

    return {
      person
    }
  }
};
</script>

<style lang="scss" scoped>
</style>