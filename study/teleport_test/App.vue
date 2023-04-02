<template>
  <h2>APP 父级组件，Teleport组件，父级组件给孙级组件发送消息</h2>
  <ModalButton />
</template>

<script lang="ts">
import ModalButton from "@/ModalButton.vue";
import {
  defineComponent
} from 'vue';

export default defineComponent({
  name: 'App',
  components:{
    ModalButton,
  },
  setup() {


    return {

    }
  }
})

</script>