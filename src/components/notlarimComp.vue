<script setup lang='ts'>
defineProps({
  changeComp: Function
})

let noteList: any = localStorage.getItem("noteList");
if (!noteList) noteList = [];
else noteList = JSON.parse(noteList)
noteList = noteList.map((a: string) => JSON.parse(a))

console.log(noteList)
</script>

<template>
  <div class="absolute w-full h-full flex justify-center align-center">
    <v-card variant="outlined" loading color="white"
      class="backdrop-blur-lg backdrop-filter break-all  w-2/3 h-5/6 p-5 overflow overflow-auto">
      <div class="w-full flex justify-end text-3xl">
        <v-btn @click="changeComp?.()" variant="outlined"> <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16"
            fill="currentColor" class="bi bi-x-lg" viewBox="0 0 16 16">
            <path
              d="M2.146 2.854a.5.5 0 1 1 .708-.708L8 7.293l5.146-5.147a.5.5 0 0 1 .708.708L8.707 8l5.147 5.146a.5.5 0 0 1-.708.708L8 8.707l-5.146 5.147a.5.5 0 0 1-.708-.708L7.293 8 2.146 2.854Z" />
          </svg></v-btn>
      </div>
      <v-expansion-panels variant="popout" class="p-5">
        <v-expansion-panel v-for="note in noteList" bg-color="transparent"
          style="white-space: pre-line;border-style:solid;border-color:white;border-width:1px;" :title="note.title"
          :text="note.content" />
      </v-expansion-panels>
    </v-card>
  </div>
</template> 
