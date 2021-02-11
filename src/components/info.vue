<template>
  <div class="info">
    <br>
    <label>Details de la carte</label>
    <br>
    <br>
    <table>
      <thead>
      <tr>
        <th class="column">Nom</th>
        <th class="column">Type</th>
        <th class="column">Description</th>
        <th class="column">race/utilisation</th>
        <th class="column">Archetype</th>
        <th class="column">prix cardmarket</th>
        <th class="column">prix tcgplayer</th>
        <th class="column">prix ebay</th>
        <th class="column">prix amazon</th>
        <th class="column">prix coolstuffinc</th>
      </tr>
      </thead>
      <tbody>
       <tr>
         <td class="column"> {{Details.data[0].name}}</td>
         <td class="column"> {{Details.data[0].type}}</td>
         <td class="column"> {{Details.data[0].desc}}</td>
         <td class="column"> {{Details.data[0].race}}</td>
         <td class="column"> {{Details.data[0].archetype}}</td>
         <td class="column"> {{Details.data[0].card_prices[0].cardmarket_price}}</td>
         <td class="column"> {{Details.data[0].card_prices[0].tcgplayer_price}}</td>
         <td class="column"> {{Details.data[0].card_prices[0].ebay_price}}</td>
         <td class="column"> {{Details.data[0].card_prices[0].amazon_price}}</td>
         <td class="column"> {{Details.data[0].card_prices[0].coolstuffinc_price}}</td>
       </tr>
      </tbody>
    </table>

    <br>
    <label>Package dans lesquelles sont présent la carte</label>
    <br>
    <br>
    <table>
      <thead>
      <tr>
        <th class="column">Nom</th>
        <th class="column">Code</th>
        <th class="column">Rareté</th>
        <th class="column">Prix</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="set in Details.data[0].card_sets">
        <td class="column">{{set.set_name}}</td>
        <td class="column">{{set.set_code}}</td>
        <td class="column">{{set.set_rarity_code}}</td>
        <td class="column">{{set.set_price}}</td>
      </tr>
      </tbody>
    </table>

    <br>
    <label>Images de la carte</label>
    <table>
      <tbody>
      <tr v-for="image in Details.data[0].card_images">
        <td v-on:click="this.href=visuliserCarte(image.image_url)"> Visualiser carte</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "details",
  data() {
    return {
      Details: [],

    };
  },
  created() {
    this.getCarte();
  },
  methods: {
    getCarte(){
      axios
          .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?language=fr&name='+this.getName())
          .then(response => (this.Details = response.data))
    },
    getName(){
      var url = decodeURI(window.location.href);
      var urlsplit = url.split("/")
      var lastpart = urlsplit[urlsplit.length-1];
      if(lastpart === '') {
        lastpart = urlsplit[urlsplit.length-2];
      }
      return lastpart
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