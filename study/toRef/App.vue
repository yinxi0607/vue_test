<template>
  <h2>toRef</h2>
  <h3>state:{{state}}</h3>
  <h3>age:{{age}}</h3>
  <h3>money:{{money}}</h3>
<hr/>
  <button @click="update">更新数据</button>
  <hr/>
  <ChildTest :age="age"/>
</template>

<script lang="ts">

import {
  defineComponent, reactive, ref, toRef,
} from 'vue';

import ChildTest from "@/components/ChildTest.vue";

export default defineComponent({
  name: 'App',
  components: {ChildTest},
  setup: function () {
    const state = reactive({
      age: 5,
      money: 10
    })
    //把响应式数据state对象中的某个属性age编程了ref对象了
    const age = toRef(state, "age")
    // 把响应式对象中的某个属性使用ref进行包装，变成了一个ref对象
    const money = ref(state.money)
    console.log(age)
    console.log(money)
    const update = () =>{
      state.age +=2
      money.value +=10
    }
    return {
      state,
      age,
      money, update
    }
  }
})


</script>