<template>
  <h2>toRaw和markRaw</h2>
  <h3>state:{{state}}</h3>

  <hr/>
  <button @click="testToRaw">测试toRaw</button>
  <button @click="testMarkRaw">测试markrRaw</button>
</template>

<script lang="ts">

import {
  defineComponent,
  markRaw,
  reactive,
  readonly,
  ref,
  shallowReactive,
  shallowReadonly,
  shallowRef,
  toRaw
} from 'vue';

interface UserInfo{
  name: string;
  age: number;
  likes?:string[];
}

export default defineComponent({
  name: 'App',
  setup() {
    const state = reactive<UserInfo>({
      name:"小明",
      age:20
    })
    const testToRaw = ()=>{
      const user = toRaw(state)
      user.name += "==="
      console.log("testToRaw")
    }
    const testMarkRaw = ()=>{
      // state.likes = ["吃","喝"]
      // state.likes[0] += "=="
      // console.log(state)

      const likes =["吃","喝"]
      state.likes = markRaw(likes)
      setInterval(()=>{
        if (state.likes){
          state.likes[0] += "-"
          console.log("定时器走起来")
        }
      },1000)
    }
    return{
      state,
      testToRaw,
      testMarkRaw,
    }
  }
})


</script>