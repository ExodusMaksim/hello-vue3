<template>
  <p>{{ msg }}</p>
  <button @click="changeMsg">修改msg</button>
  <input type="text" v-model="tagsStr" placeholder="输入标签，用英文逗号隔开" />
</template>

<script lang="ts">
import { defineComponent, onMounted, ref, watch, computed } from 'vue'

export default defineComponent({
  setup() {
    const msg = ref<string>('Hello World')
    function changeMsg() {
      msg.value = 'Hi World'
    }

    const init = () => {
      console.log('init')
    }

    onMounted(() => {
      init()
    })

    watch(
      msg,
      () => {
        console.log('触发监听', msg.value)
      },
      {
        immediate: true,
      }
    )

    const tags = ref<string[]>([])
    const tagsStr = computed({
      get() {
        return tags.value.join(',')
      },
      set(newValue: string) {
        tags.value = newValue.split(',')
      },
    })

    return {
      msg,
      changeMsg,
      tagsStr,
    }
  },
})
</script>
<style module>
.msg {
  font-size: 14px;
}
</style>
