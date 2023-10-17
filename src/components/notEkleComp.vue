<script setup lang='ts'>
defineProps(["changeNotEkleCompBool"])
</script>

<template>
  <div class="absolute w-full h-full flex justify-center align-center">
    <v-card variant="outlined" loading color="white" class="backdrop-blur-lg backdrop-filter p-6 w-1/3">
      <v-text-field label="Başlık" :rules="[
        value => !!value || 'Gerekli.',
        value => (value && value.length >= 3) || 'En az 3 karakter',
      ]" variant="outlined" hide-details="auto"></v-text-field>
      <v-textarea label="İçerik" :rules="[
        value => !!value || 'Gerekli.',
        value => (value && value.length >= 3) || 'En az 3 karakter',
      ]" variant="outlined" hide-details="auto">
      </v-textarea>
      <v-btn block variant="outlined">Ekle</v-btn>
      <span class="text-sm font-italic text-center w-full">çıkmak için ESC</span>
    </v-card>
  </div>
</template> 
