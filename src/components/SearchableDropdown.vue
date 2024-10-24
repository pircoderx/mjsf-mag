<script setup>
import { ref } from 'vue';
const props = defineProps({
  'items': {
    type: Array,
    default: []
  }
});
const format = defineModel({ default: '' });
function filtrate(format) {
  format = format.toLowerCase();
  return props.items.filter(
    (item) => item.value.toLowerCase().startsWith(format)
  );
}
</script>
<template>
  <div class="border-4 border-black p-1">
    <input class="w-full text-center" type="text" placeholder="Filter"
           v-model="format" />
    <div v-for="item in filtrate(format)"
         class="border-t-2 border-black">
      <button class="w-full" @click="$emit('submit', item)">
        {{ item.value }}
      </button>
    </div>
    <div v-if="filtrate(format).length == 0"
         class="border-t-2 border-black text-center">
      Nothing ):
    </div>
  </div>
</template>

