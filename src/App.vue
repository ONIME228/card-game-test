<template>
  <main>
    <div class="overlay-wrapper">
      <CardWrapper/>
      <button @click="handleClick" class="button"> Click me </button>
    </div>
  </main>
</template>
<script setup>
import { provide, ref } from 'vue';
import CardWrapper from './CardWrapper.vue';
import { IS_CLICKED } from './constants.js';

const isClicked = ref(false);
provide(IS_CLICKED, isClicked);
const handleClick = () => {
  isClicked.value = true;
}
</script>


<style scoped>
.overlay-wrapper {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 24px;
}
.button {
   width: 64px;
   height: 64px;
   border-radius: 32px;
   cursor: pointer;
}
@media (max-width: 600px) {
  .button {
    width: 120px;
    height: 120px;
   border-radius: 60px;
   font-size: 32px;
   margin-bottom: 12px;

  }
}
</style>
