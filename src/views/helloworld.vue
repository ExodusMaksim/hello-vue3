<template>
  <p class="msg">{{ msg }}</p>
</template>

<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue'
import Child from "@cp/Child.vue"

export default defineComponent({
  components: {
    Child
  },
  setup() {
    const msg = ref<HTMLElement | null>(null)
    const child = ref<typeof Child | null>(null)

    onMounted(() => {
      console.log(msg.value?.innerText)
      child.value.isShowDialog = true
    })

    return {
      msg,
      child,
    }
  },
})
</script>

<style scoped>
.msg {
  font-size: 14px;
}
</style>
