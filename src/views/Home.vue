<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <div>home</div>
    <p>{{data()}}</p>
  </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'

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