<script setup>
import Button from './components/Button.vue';
import SearchableDropdown from './components/SearchableDropdown.vue';
import { ref } from 'vue';
const count = ref(0);
const selected = ref('');
const fruits = [ 'Apple', 'Avocado'
               , 'Banana', 'Lemon', 'Orange'
               , 'Peach', 'Pear' ];
const fruit_items = fruits.map((e, i) => ({ value: e, index: i }));
</script>

<template>
  <Button label="Button A" color="red" size="middle" icon="vite.svg" />
  <Button :label="'Count: ' + count" color="green" size="big"
          @push="++count" />
  <Button label="Button C" color="blue" size="small" />
  <SearchableDropdown :items="fruit_items"
                      @submit="(item) => selected = item.value" />
  <div>
    Selected: {{ selected }}
  </div>
</template>

