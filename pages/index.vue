<template>
  <div class="container mx-auto">
    <buttons />
    <div class="mt-8">
      <div class="flex justify-end">
        <div class="text-white page-title">تمام دوره ها</div>
      </div>
      <div class="flex justify-end mt-1">
        <underLine />
      </div>
    </div>
    <div>
      <allCategories/>
    </div>
  </div>
</template>

<script>
import allCategories from '~/components/allCategories/allCategories.vue'
export default {
  components: { allCategories },
  name: 'IndexPage',
}
</script>
