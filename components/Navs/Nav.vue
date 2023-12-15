<script setup>
const isOpen = ref(false);
</script>

<template>
  <nav>
    <div
      class="flex bg-black justify-between items-center p-8"
    >
      <div class="">
        <nuxt-link class="" to="/">
          <slot name="logo"> </slot>
        </nuxt-link>
      </div>
      <div class="">
        <ul
          class="hidden md:flex space-x-8 text-[#4FC0D0] text-xl"
        >
          <slot name="links"></slot>
        </ul>
        <ul class="flex md:hidden">
          <li class="">
            <button type="button" @click="isOpen = !isOpen">
              <i v-if="!isOpen" class="ri-menu-line text-3xl"></i>
              <i v-else class="ri-close-line text-4xl"></i>
            </button>
          </li>
        </ul>
      </div>
    </div>
    <div class="" v-if="isOpen">
      <ul
        class="md:hidden flex flex-col py-8 px-4 space-y-2 border-b border-white bg-gray-200/75 text-[#4FC0D0] transition-all text-xl"
      >
        <slot name="links"></slot>
      </ul>
    </div>
  </nav>
</template>
