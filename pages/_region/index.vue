<template>
  <div class="container">
    <v-toolbar color="teal lighten-3">
      <v-btn color="rgb(255, 0, 0, 0.01)" to="/">
        <v-icon>keyboard_return</v-icon>
      </v-btn>
      <v-text-field
        style="margin-top: 4.5%; margin-left: 5%; margin-right: 5%"
        label="Search"
        v-model="searchCountryItem"
        outlined
        placeholder="country"
      >
      </v-text-field>
      <v-badge left color="secondary">
        <v-icon>flag</v-icon>
        <h1 style="color: green" slot="badge">
          {{ regionCountryList.length }}
        </h1>
      </v-badge>
    </v-toolbar>
    <v-app wrap>
      <!-- country list start -->
      <span v-if="searchFilterByCountry == 0" style="text-align: center">
        <v-chip class="ma-2" color="warning"> No search found </v-chip>
      </span>
      <v-container fluid>
        <v-row>
          <v-col
            sm="6"
            md="4"
            xs="12"
            lg="4"
            v-for="(country, i) in searchFilterByCountry"
            :key="i"
          >
            <router-link
              :to="{ path: `/${region}/` + country.name }"
              style="text-decoration: none"
            >
              <v-card class="mx-auto" max-width="344">
                <v-list-item three-line>
                  <v-list-item-content>
                    <div class="overline mb-4">
                      {{ country.name }}({{ country.currency }})
                    </div>
                    <span style="display: flex">
                      <v-icon>person</v-icon>
                      <v-list-item-title class="mb-1">{{
                        country.population.toLocaleString("en-US", {
                          maximumFractionDigits: 2,
                        })
                      }}</v-list-item-title>
                    </span>
                  </v-list-item-content>
                  <img
                    :src="country.flag"
                    height="100%"
                    width="100px"
                    style="border-radius: 15%"
                  />
                </v-list-item>
              </v-card>
            </router-link>
          </v-col>
        </v-row>
      </v-container>
    </v-app>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: `Region | ${this.region}`,
    };
  },
  data() {
    return {
      region: this.$route.params.region,
      regionCountryList: [],
      searchCountryItem: "",
      snackbar: true,
    };
  },
  created() {
    this.regionCountryList = [];
    this.$axios
      .get(`https://restcountries.eu/rest/v2/region/${this.region}`)
      .then((res) => {
        res.data.forEach((country) => {
          this.regionCountryList.push({
            name: country.name,
            flag: country.flag,
            currency: country.currencies[0].symbol,
            population: country.population,
          });
        });
        console.log(this.regionCountryList);
      })
      .catch((err) => {
        console.log(err);
      });
  },

  computed: {
    searchFilterByCountry: function () {
      return this.regionCountryList.filter((country) => {
        return country.name.match(this.searchCountryItem);
      });
    },
  },
};
</script>

<style scoped></style>
