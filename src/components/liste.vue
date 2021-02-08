<template>
  <div class="liste">
    <table>
      <thead>
      <tr>
        <th class="column">Nom</th>
        <th class="column">Type</th>
        <th class="column">Description</th>
        <th class="column">Race/Fonctionnement</th>
        <th class="column">Rareté</th>
        <th class="column">Image</th>
      </tr>
      </thead>

      <tbody>
      <tr v-for="carte in listeCarte.data" :key="carte.id">
        <td v-on:click="this.href=getDetails(carte.name)">{{carte.name}}</td>
        <td >{{carte.type}}</td>
        <td>{{carte.desc}}</td>
        <td>{{carte.race}}</td>
        <td>{{carte.card_sets[0].set_rarity}}</td>
        <td v-on:click="this.href=visuliserCarte(carte.card_images[0].image_url)"> Visualiser carte</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import router from "@/router";

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
                .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?language=fr&num=5&offset=0')
                .then(response => (this.listeCarte = response.data))
          },
    getDetails(name){
      router.go("/details/"+name);
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