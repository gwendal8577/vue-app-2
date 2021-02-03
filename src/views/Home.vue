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
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'
export default {
  name: "home",
  info: [],
  mounted(){
    axios
        .get('https://db.ygoprodeck.com/api/v7/cardinfo.php')
        .then(response => (this.info = response))
  },
  methods: {
    data(){
      console.log(this.info)
      return(this.info)
    }
  }
}
</script>