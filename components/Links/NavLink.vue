<script setup>
const props = defineProps({
  to: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <NuxtLink
    :to="to"
    class="text-lg text-bold text-[#c2efb3] hover:text-scale-2xl font-sans "
    active-class=""
  >
    <slot />
  </NuxtLink>
</template>
