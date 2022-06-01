<template>
  <h1>Ma Méteo</h1>
  <div class="prevision">Previsions</div>
  <br />
  <form @submit.prevent="getWeather">
    <div>
      <label>city</label>
      <!-- <input v-model.trim="city" /> -->
      <select v-model.trim="city" name="ville" id="ville">
        <option value="">Choisir ville</option>
        <option value="Marseille">Marseille</option>
        <option value="Nice">Nice</option>
      </select>
    </div>
    <button type="submit">Resultats</button>
  </form>
  <br />
  <div>
    Details
    <p>Ressenti: {{ result.feels_like }}</p>
    <p>humidité: {{ result.humidity }}</p>
    <p>pression: {{ result.pressure }}</p>
    <p>temperature: {{ result.temp }}</p>
    <p>Max: {{ result.temp_max }}</p>
    <p>Min: {{ result.temp_min }}</p>
  </div>
  <br />

  <div class="">
    Vitesse du vent
    <p>speed:{{ result2.speed }}</p>
    <p>deg: {{ result2.deg }}</p>
    <p>gust:{{ result2.gust }}</p>
  </div>
</template>

<script>
// fetch(
//   "https://api.openweathermap.org/data/2.5/forecast?lat={lat}&lon={lon}&appid={eb69be890b7e8149dd77e277f7ad1a40}"
// )
//   .then((response) => {
//     response.json();
//   })
//   .catch((error) => {
//     alert("Erreur: " + error);
//   });

const APIKEY = "eb69be890b7e8149dd77e277f7ad1a40";
export default {
  name: "App",
  data() {
    return {
      city: "",
      result: {},
      result2: {},
    };
  },
  methods: {
    async getWeather() {
      if (!this.city) {
        return;
      }
      const res = await fetch(
        `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${APIKEY}&units=metric`
        // `http://api.openweathermap.org/geo/1.0/direct?q=Marseille&limit=5&appid={APIKEY}`
      );
      const { main } = await res.json();
      this.result = main;

      const rese = await fetch(
        `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&appid=${APIKEY}&units=metric`
      );

      const { wind } = await rese.json();
      this.result2 = wind;

      // console.log(this.result);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
