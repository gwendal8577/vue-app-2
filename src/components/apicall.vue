<template>
  $END$
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.component('apiCall', {
  data: function () {
    return {
      info: null
    }
  },
  mounted () {
    axios
        .get('https://db.ygoprodeck.com/api/v7/cardinfo.php')
        .then(response => (this.info = response))
  }
})
new Vue({
  el: '#app',
  data () {
    return {
      info: null
    }
  },
  mounted () {
    axios
        .get('https://db.ygoprodeck.com/api/v7/cardinfo.php')
        .then(response => (this.info = response))
  }
})
</script>

<style scoped>
</style>