<template>
  <SearchInput />
  <div class="singleCountry" v-if="show_country">
    <p>Country</p>
    <button @click="showAllCountries">Back</button>
  </div>
  <div class="hello" v-else>
    <!-- <div v-for="job in jobs" :key="job.id">{{ job.title }}</div> -->
    <div
      class="country-card"
      v-for="country in countries"
      :key="country.name"
      @click="showCountry(country.alpha2Code)"
    >
      <div class="country-flags">
        <img :src="country.flags.svg" :alt="country.name" class="flag" />
      </div>

      <div class="country-info">
        <h3 class="name">
          {{ country.name }}
        </h3>
        <div class="population">
          <span>Population:</span> {{ country.population }}
        </div>
        <div class="region"><span>Region:</span> {{ country.region }}</div>
        <div class="capital"><span>Capital:</span> {{ country.capital }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchInput from "./SearchInput.vue";
export default {
  name: "AllCountries",
  data() {
    return {
      // jobs: [
      //   { title: "UX Designer", id: 1, details: "lorem" },
      //   { title: "Web Developer", id: 2, details: "lorem" },
      //   { title: "Vue Developer", id: 3, details: "lorem" },
      // ],
      countries: [],
      country: {},
      show_country: false,
    };
  },
  components: {
    SearchInput,
  },
  methods: {
    fetchCountries: function () {
      let allCountries = "https://restcountries.com/v2/all";
      axios.get(allCountries).then((res) => {
        this.countries = res.data;
        console.log(this.countries);
      });
    },
    showCountry: function (alphacode) {
      let allCountries = this.countries;
      let country = allCountries.filter(
        (country) => country.alpha2Code == alphacode
      );
      this.country = country;
      this.show_country = true;
    },
    showAllCountries: function () {
      this.show_country = false;
    },
  },
  mounted() {
    this.fetchCountries();
  },
  props: {
    msg: String,
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

.hello {
  padding: 50px;
  display: grid;
  grid-template-columns: repeat(4, auto);
  grid-row-gap: 50px;
  grid-column-gap: 40px;
}

.country-card {
  /* width: 300px; */
  font-family: "Nunito Sans", sans-serif;
  font-size: 14px;
  box-shadow: rgba(0, 0, 0, 0.24) 0px 3px 8px;
  border-radius: 10px;
  cursor: pointer;
  transition: transform 300ms ease;
}

.country-card:hover {
  transform: scale(1.05);
}

.country-flags {
  /* width: 200px; */
}

.flag {
  width: 100%;
  height: 160px;
  border-top-right-radius: 10px;
  border-top-left-radius: 10px;
}

.country-info {
  text-align: left;
  padding: 25px;
  background: #fff;
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
}

.name {
  margin-bottom: 15px;
}
</style>
