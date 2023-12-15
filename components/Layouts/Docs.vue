<template>
  <LayoutsBase>
    <template #navigation>
      <Nav/>
    </template>

    <template #content>
      <slot />
    </template>

    <template #footer>
      <FootersBasic />
    </template>
  </LayoutsBase>
</template>
