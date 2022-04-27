<template>
<div class="container mx-auto">
  <div class="md:hidden"><nuxtLink to="mobileButton"><mobileMenuBtn/></nuxtLink></div>
  <div class="hidden md:block"><buttons/></div>
  <Nuxt />
</div>
</template>

<script>
import mobileMenuBtn from '~/components/mobileMenuBtn.vue'
export default {
  components: { mobileMenuBtn },

}
</script>

<style>

</style>