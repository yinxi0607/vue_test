<template>
  <h2>shallowReactive和shallowRef</h2>
  <h3>m1:{{m1}}</h3>
  <h3>m2:{{m2}}</h3>
  <h3>m3:{{m3}}</h3>
  <h3>m4:{{m4}}</h3>
  <hr/>
  <button @click="update">更新数据</button>
</template>

<script lang="ts">

import {defineComponent, reactive, ref, shallowReactive, shallowRef} from 'vue';


export default defineComponent({
  name: 'App',
  setup() {
    // 深度劫持（深监视）---深度响应式
    const m1 = reactive({
      name: "小红",
      age:20,
      cat:{
        name: '奔驰',
        color:'red'
      }
    })
    // 浅劫持（浅监视）---浅响应
    const m2 = shallowReactive({
      name: "小红",
      age:20,
      cat:{
        name: '奔驰',
        color:'red'
      }
    })
    // 深度劫持（深监视）---深度响应式 reactive的处理
    const m3 = ref({
      name: "小红",
      age:20,
      cat:{
        name: '奔驰',
        color:'red'
      }
    })
    
    const m4 = shallowRef({
      name: "小红",
      age:20,
      cat:{
        name: '奔驰',
        color:'red'
      }
    })
    const update =()=>{
      // 更改m1的数据---reactive方式
      // m1.name += "=="
      // m1.cat.name += "--"
      // 更改m2的数据---shallowReactive方式
      // m2.name += "=="
      // m2.cat.name += "--"
      // 更改m3的数据---ref方式
      // m3.value.name += "=="
      // m3.value.cat.name += '--'
      // // 更改m4的数据---shallowRef方式
      m4.value.name += "=="
      // m4.value.cat.name += "--"
    }
    return{
      m1,m2,m3,m4,
      update,
    }
  }
})


</script>