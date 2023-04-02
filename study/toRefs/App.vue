

<template>
  <h2>toRefs的使用</h2>
  <!--  <h3>name:{{ state.name }}</h3>-->
  <!--  <h3>age:{{ state.age }}</h3>-->
  <h3> name: {{ name }}</h3>
  <h3> age: {{ age }}</h3>
  <h3> name2: {{ name2 }}</h3>
  <h3> age2: {{ age2 }}</h3>
</template>

<script lang="ts">

import {defineComponent, reactive, toRefs} from 'vue';

function useFeatureX(){
  const state = reactive({
    name2: "自来也",
    age2: 89
  })
  return{
    ...state
  }
}

export default defineComponent({
  name: 'App',
  setup() {
    const state = reactive({
      name: "自来也",
      age: 48
    })
    // toRefs 可以把一个响应式的对象转化成普通对象，该普通对象的每个property都是一个ref
    // const state2 = toRefs(state)
    const {name,age} = toRefs(state)
    // 定时器，更新数据（如果数据变化了，界面也随之变化，肯定是响应式的数据）
    setInterval(() => {
      // state.age += 1
      // state2.age.value += 1
      age.value +=1
    }, 1000)

    const {name2,age2} = useFeatureX()
    return {
      // state,
      // ...state //不是响应式的数据了 ---> {name:"自来也"，age:47}
      // ...state2
      name,age
      ,name2,age2
    }
  }
})


</script>

