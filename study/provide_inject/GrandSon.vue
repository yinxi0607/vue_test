<template>
<h3 :style="{color}">GrandSon 孙子组件</h3>

</template>

<script lang="ts">
import {inject} from "vue";

export default {
  name: "GrandSon",
  setup(){
    const color = inject("color")
    return{
      color
    }
  }
}
</script>

<style scoped>

</style>