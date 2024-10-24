<script setup>
import Button from './components/Button.vue';
import { ref } from 'vue';
const count = ref(0);
</script>

<template>
  <Button label="Button A" color="red" size="middle" icon="vite.svg" />
  <Button :label="'Count: ' + count" color="green" size="big"
          @push="++count" />
  <Button label="Button C" color="blue" size="small" />
</template>

