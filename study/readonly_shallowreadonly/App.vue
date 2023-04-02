<template>
  <h2>shallowReadonly和readonly</h2>
  <h3>state:{{state2}}</h3>

  <hr/>
  <button @click="update">更新数据</button>
</template>

<script lang="ts">

import {defineComponent, reactive, readonly, ref, shallowReactive, shallowReadonly, shallowRef} from 'vue';


export default defineComponent({
  name: 'App',
  setup() {
    const state = reactive({
      name : "小左",
      age : 20,
      cat:{
        name:"奔驰",
        color:"yellow"
      }
    })
    // readonly 只读数据，深度只读
    // const state2 = readonly(state)
    // 只读的数据，浅只读
    const state2 = shallowReadonly(state)
    const update=()=>{
      state2.cat.name += "--"
    }
    return{
      state2,
      update,
    }
  }
})


</script>