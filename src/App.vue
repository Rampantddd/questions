<script lang="ts" setup>
import {ref} from "vue";
import Son from "./components/son.vue";
import Bother from "./components/bother.vue";

window.addEventListener("scroll", () => {
  debounceScroll(123)
})

const debounce = <A extends any[], R>(fn: (...arg: A) => R, delay?: number): (...arg: A) => void => {
  let timer: number | null = null
  return function (...arg: A) {
    if (timer) {
      clearInterval(timer)
    }
    timer = setTimeout(() => fn(...arg), delay)
  }
}

const bodyScroll = (num: number) => {
  console.log(document.body.scrollTop || document.documentElement.scrollTop)
  console.log("数字:" + num)
}

const debounceScroll = debounce(bodyScroll, 1000)

const mes = ref('my child')

const update = (res: string) => {
  console.log(res);
}

</script>
<template>
  <son v-model="mes" @update:model-value="update"></son>
  <bother></bother>
</template>
<style scoped>
ul li {
  height: 100px;
}
</style>