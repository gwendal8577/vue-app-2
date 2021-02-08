<template>
  <div class="home">
    <Details></Details>
  </div>
</template>

<script>
import details from '../components/details.vue'
export default {
  name: "details",
  props: "name",
  components: {
    details
  }
}
</script>

<style scoped>
</style>