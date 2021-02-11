<template>
  <div class="liste">
    <table>
      <thead>
      <tr>
        <th class="column">Nom</th>
        <th class="column">Image</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="carte in listeCarte.data" :key="carte.id">
        <router-link :to="'/details/' + carte.name">
          <td>
            {{carte.name}}
          </td>
        </router-link>
        <td v-on:click="this.href=visuliserCarte(carte.card_images[0].image_url)"> Visualiser carte</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: "liste",
  data(){
    return {
      listeCarte: [],
    };
  },
  created() {
    this.getList();
  },
  methods: {
    getList(){
            axios
                .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?language=fr')
                .then(response => (this.listeCarte = response.data))
          },
    visuliserCarte(carte){
      document.location.href=carte
    },
  },
}
</script>

<style scoped>
table {
  border-collapse:collapse;
}
td {
  border:solid 1px #808080;
}
</style>