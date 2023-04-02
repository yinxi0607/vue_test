<template>
  <h2>响应式数据的判断</h2>

</template>

<script lang="ts">

import {
  defineComponent, isProxy, isReactive, isReadonly, isRef, provide, reactive, readonly, ref,
} from 'vue';
export default defineComponent({
  name: 'App',
  setup() {
    // isRef:检查一个值是否为一个 ref 对象
    // isReactive:检查一个对象是否是由 reactive创建的响应式代理
    // isReadonly:检查一个对象是否是由 readonly创建的只读个我理
    // isProxy:检查一个对象是否是由 reactive或者 readonly方法创建的代理

    console.log(isRef(ref({})))
    console.log(isReactive(reactive({})))
    console.log(isReadonly(readonly({})))
    console.log(isProxy(readonly({})))
    console.log(isProxy(reactive({})))

    return {

    }
  }
})

</script>