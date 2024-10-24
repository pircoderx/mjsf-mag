<script setup>
const props = defineProps({
  label: { type: String, default: 'Button' },
  color: { type: String, default: 'red' },
  size: { type: String, default: 'middle' },
  icon: { type: String }
});
defineEmits(['push']);
function get_style() {
  const htab = {'small': 'h-7', 'middle': 'h-14', 'big': 'h-28'};
  const ctab = {
    'red': ['bg-red-700', 'border-red-900'],
    'green': ['bg-green-700', 'border-green-900'],
    'blue': ['bg-blue-700', 'border-blue-900']
  };
  const height = Object.hasOwn(htab, props.size)
                 ? htab[props.size] : 'h-14';
  const bg = Object.hasOwn(ctab, props.color)
             ? ctab[props.color][0] : 'bg-red-700';
  const border = Object.hasOwn(ctab, props.color)
               ? ctab[props.color][1] : 'border-red-900';
  return 'content-center text-center text-white border-2 w-full'
       + ' ' + height + ' ' + bg + ' ' + border;
}
</script>

<template>
  <button @click="$emit('push')" type="button" :class="get_style()">
    <img v-if="icon" class="inline-block object-scale-down max-h-full m-auto" :src="icon" />
    <div class="inline-block">{{label}}</div>
  </button>
</template>

