<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <div>
      <p>
        {{ data() }}
      </p>
    </div>
  </div>
</template>

<script>
import liste from './components/liste.vue'
export default {
  name: "home"
}
</script>