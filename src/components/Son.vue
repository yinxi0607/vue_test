<template>
<h3>Son 子级组件</h3>
  <hr/>
  <GrandSon />
</template>

<script lang="ts">
import {defineComponent} from "vue";
import GrandSon from './GrandSon'
export default {
  name: "SonTest",
  components:{
    GrandSon
  }
}
</script>

<style scoped>

</style>