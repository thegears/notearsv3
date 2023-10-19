<script setup lang='ts'>
const props = defineProps({
  changeComp: Function
});
import { ref } from 'vue'

const title = ref();
const content = ref();


const notEkleSuccess = ref(false);
const notEkleError = ref(false);

async function onFormSubmit(e: any) {
  e.preventDefault();

  if ((!title.value) || (!content.value)) {
    notEkleSuccess.value = false;
    notEkleError.value = true
    return false;
  }


  let noteList: any = localStorage.getItem("noteList");
  if (!noteList) noteList = [];
  else noteList = JSON.parse(noteList)

  noteList.push(JSON.stringify({
    title: title.value,
    content: content.value,
    date: new Date().toLocaleDateString('tr-TR', { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric', hour: 'numeric', minute: 'numeric' })
  }));

  localStorage.setItem("noteList", JSON.stringify(noteList));
  notEkleError.value = false
  notEkleSuccess.value = true
  props.changeComp?.()

  title.value = ''
  content.value = ''

}


</script>

<template>
  <div class="absolute w-full h-full flex justify-center align-center">
    <v-card variant="outlined" loading color="white" class="backdrop-blur-lg backdrop-filter w-1/3 p-5">
      <div class="w-full flex justify-end text-3xl">
        <v-btn @click="changeComp?.()" variant="outlined"> <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16"
            fill="currentColor" class="bi bi-x-lg" viewBox="0 0 16 16">
            <path
              d="M2.146 2.854a.5.5 0 1 1 .708-.708L8 7.293l5.146-5.147a.5.5 0 0 1 .708.708L8.707 8l5.147 5.146a.5.5 0 0 1-.708.708L8 8.707l-5.146 5.147a.5.5 0 0 1-.708-.708L7.293 8 2.146 2.854Z" />
          </svg></v-btn>
      </div>
      <v-form @submit="onFormSubmit" class="p-5">
        <v-text-field error-messages="" v-model="title" name="title" label="Başlık" variant="outlined" class='mb-2'
          hide-details="auto" />
        <v-textarea v-model='content' name="content" label="İçerik" variant="outlined" class='mb-2' hide-details="auto" />
        <v-btn type="submit" block variant="outlined">Ekle</v-btn>

        <v-snackbar v-model="notEkleSuccess" :timeout="2000" color="success" variant="outlined">
          Not başarıyla <strong>eklendi.</strong>
        </v-snackbar>

        <v-snackbar v-model="notEkleError" :timeout="2000" color="error" variant="outlined">
          Lütfen eksiksiz <strong>doldurun.</strong>
        </v-snackbar>

      </v-form>
    </v-card>
  </div>
</template> 


