<template>

</template>

<script>
import axios from 'axios'
export default {
  name: "liste",
  info: [],
  data(){
    return(this.info)
  },
  mounted(){
    axios
        .get('https://db.ygoprodeck.com/api/v7/cardinfo.php')
        .then(response => (this.info = response.data))
  },
}
</script>

<style scoped>

</style>