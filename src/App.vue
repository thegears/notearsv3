<script setup lang="ts">
import SiteTitle from './components/SiteTitle.vue'
import notlarimComp from './components/notlarimComp.vue'
import notEkleComp from './components/notEkleComp.vue'
import { ref } from 'vue'

function changeBgColor(a: number, b: number, c: number) {
  document.querySelector("body")!.style["background-color" as any] = `rgb(${a},${b},${c})`
}

window.document.body.onkeydown = (e) => {
  if (e.key == "Escape" && (notEkleCompBool.value || notlarimCompBool.value)) {
    changeComp("")
  }
}

changeBgColor(10, 10, 10)
const bgOpacity = ref(false)

const notEkleCompBool = ref(false)
const notlarimCompBool = ref(false)

function changeComp(comp: string) {

  if (comp == 'notEkle') {
    notEkleCompBool.value = true
    bgOpacity.value = true
    changeBgColor(10, 18, 10)
  } else if (comp == "notlarim") {
    notlarimCompBool.value = true
    bgOpacity.value = true
    changeBgColor(18, 18, 10)

  } else {
    bgOpacity.value = false
    notEkleCompBool.value = false
    notlarimCompBool.value = false
    changeBgColor(18, 18, 18)
  }
}
</script>

<template>
  <div>
    <transition name="slide-fade">
      <SiteTitle :class="{ 'opacity-10': bgOpacity }" :changeComp="changeComp" />
    </transition>

    <transition name="slide-fade">
      <notEkleComp v-if="notEkleCompBool" :changeComp="changeComp" />
    </transition>

    <transition name="slide-fade">
      <notlarimComp v-if="notlarimCompBool" :changeComp="changeComp" />
    </transition>
  </div>
</template>

<style>
/*
  Enter and leave animations can use different
  durations and timing functions.
*/
.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.5s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}
</style>

