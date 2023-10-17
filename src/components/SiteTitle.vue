<script setup lang="ts">
defineProps(["changeComp"])

</script>

<template>
  <div class="center">
    <h1>
      <span className="cursor-default">Notears</span>

      <span className="cursor-default">Notears</span>
      <span className="cursor-default">Notears</span>
    </h1>

    <p className="mt-32 text-white text-3xl">not tutmanın basit hali.</p>
    <div class="flex justify-around">
      <v-tooltip text="Notlarım">
        <template v-slot:activator="{ props }">
          <transition name="ft" appear>
            <v-btn @click="() => { changeComp('notlarim') }" v-bind="props" variant="outlined" color="yellow"><svg
                xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-stickies"
                viewBox="0 0 16 16">
                <path d="M1.5 0A1.5 1.5 0 0 0 0 1.5V13a1 1 0 0 0 1 1V1.5a.5.5 0 0 1 .5-.5H14a1 1 0 0 0-1-1H1.5z" />
                <path
                  d="M3.5 2A1.5 1.5 0 0 0 2 3.5v11A1.5 1.5 0 0 0 3.5 16h6.086a1.5 1.5 0 0 0 1.06-.44l4.915-4.914A1.5 1.5 0 0 0 16 9.586V3.5A1.5 1.5 0 0 0 14.5 2h-11zM3 3.5a.5.5 0 0 1 .5-.5h11a.5.5 0 0 1 .5.5V9h-4.5A1.5 1.5 0 0 0 9 10.5V15H3.5a.5.5 0 0 1-.5-.5v-11zm7 11.293V10.5a.5.5 0 0 1 .5-.5h4.293L10 14.793z" />
              </svg></v-btn>
          </transition>
        </template>
      </v-tooltip>
      <v-tooltip text="Not Ekle">
        <template v-slot:activator="{ props }">
          <transition name="ft" appear>
            <v-btn @click="() => { changeComp('notEkle') }" v-bind="props" variant="outlined" color="green"><svg
                xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-plus-square"
                viewBox="0 0 16 16">
                <path
                  d="M14 1a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1h12zM2 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2H2z" />
                <path
                  d="M8 4a.5.5 0 0 1 .5.5v3h3a.5.5 0 0 1 0 1h-3v3a.5.5 0 0 1-1 0v-3h-3a.5.5 0 0 1 0-1h3v-3A.5.5 0 0 1 8 4z" />
              </svg></v-btn>
          </transition>
        </template>
      </v-tooltip>
      <v-tooltip text="thegears">
        <template v-slot:activator="{ props }">
          <transition name="ft" appear>
            <v-btn v-bind="props" variant="outlined" color="white"><svg xmlns="http://www.w3.org/2000/svg" width="16"
                height="16" fill="currentColor" class="bi bi-github" viewBox="0 0 16 16">
                <path
                  d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.012 8.012 0 0 0 16 8c0-4.42-3.58-8-8-8z" />
              </svg></v-btn>
          </transition>
        </template>
      </v-tooltip>
    </div>
  </div>
</template>

<style>
.center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: prespective(1000px) translate(-50%, -50%);
  transform: skewY(15deg);
  transition: 0.2s;
}

.center:hover {
  transform: prespective(1000px) translate(-50%, -50%);
  transform: skewY(0deg);
}

.center h1 span {
  position: absolute;
  top: 0;
  left: 0;
  transform: translate(-50%, -50%);
  margin: 0;
  padding: 0;
  text-transform: uppercase;
  font-size: 12em;
  color: #fff;
  transform-style: preserve-3d;
  transition: 0.4s;
}

.center h1 span:nth-child(1) {
  clip-path: polygon(0 0, 100% 0, 100% 45%, 0 45%);
}



.center h1 span:nth-child(2) {
  color: #5E17EB;
  transform: translate(-50%, -50%) skewX(-60deg);
  left: -38px;
  clip-path: polygon(0 45%, 100% 45%, 100% 55%, 0 55%);
}

.center h1 span:nth-child(3) {
  transform: translate(-50%, -50%) skewY(0deg);
  left: -76px;
  clip-path: polygon(0 55%, 100% 55%, 100% 100%, 0 100%);
}

.center:hover h1 span:nth-child(2),
.center:hover h1 span:nth-child(3) {
  transform: translate(-50%, -50%) skewX(0deg);
  left: 0;
  color: #fff;
}

.ft-enter-active {
  animation: bounce-in 0.5s;
}

.ft-leave-active {
  animation: bounce-in 0.5s reverse;
}

@keyframes bounce-in {
  0% {
    transform: scale(1);
  }

  50% {
    transform: scale(2);
  }

  100% {
    transform: scale(1);
  }
}
</style>
