<template>
  <h2>Child子级组件</h2>
  <h4>age: {{ age }}</h4>
  <h4>length:{{length}}</h4>
  <button @click="changeMsg">更新数据</button>
</template>

<script lang="ts">
import {computed, defineComponent, Ref, toRef} from 'vue';
function useGetLength(age:Ref){
  return computed(()=>{
    return age.value.toString().length
  })
}
export default defineComponent({
  name: 'ChildTest',
  props: {
    age: {
      type: Number,
      required: true
    }
  },
  setup(props) {
    const length = useGetLength(toRef(props,"age"))

    return {
      length
    }
  }
});
</script>

