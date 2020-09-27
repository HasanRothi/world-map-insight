<template>
  <div class="container">
    <v-toolbar dense>
      {{ countryName }}
      <v-spacer></v-spacer>
      <v-icon>person</v-icon>
      {{
        countryInfo[0].population.toLocaleString("en-US", {
          maximumFractionDigits: 2,
        })
      }}

      <v-spacer></v-spacer>
      <img
        :src="countryInfo[0].flag"
        height="100%"
        width="100px"
        style="border-radius: 25%"
      />
    </v-toolbar>
    <v-app>
      <v-content class="pa-16">
        <v-card class="mx-auto" max-width="344" color="cyan lighten-5">
          <v-card-text>
            <v-card style="text-align: center">
              <span>
                <v-icon>place</v-icon>
                <div>{{ countryInfo[0].capital }}</div>
              </span>
            </v-card>
            <v-row>
              <v-col>
                <v-card class="pa-4 headline-1" style="text-align: center">
                  <h1 class="text--primary">
                    {{ countryInfo[0].topLevelDomain[0] }}
                  </h1>
                </v-card></v-col
              >
              <v-col
                ><v-card class="pa-4" style="text-align: center"
                  ><span style="display: flex">
                    <v-icon>language</v-icon>
                    <h1>{{ countryInfo[0].languages[0].nativeName }}</h1>
                  </span>
                </v-card></v-col
              >
            </v-row>
            <v-card>
              <v-row>
                <v-col>
                  <v-car
                    ><span style="display: flex">
                      <v-icon>call</v-icon>
                      <div>{{ countryInfo[0].callingCodes[0] }}</div>
                    </span></v-car
                  ></v-col
                >
                <v-col>
                  <span style="display: flex">
                    <v-icon>crop_square</v-icon>
                    <div>
                      {{
                        countryInfo[0].area.toLocaleString("en-US", {
                          maximumFractionDigits: 2,
                        })
                      }}
                      Sq km
                    </div>
                  </span></v-col
                >
              </v-row>
            </v-card>
          </v-card-text>
          <v-card-actions>
            <v-btn
              text
              color="deep-purple accent-4"
              @click="this.$router.go(-1)"
            >
              <v-icon>keyboard_return</v-icon></v-btn
            >
          </v-card-actions>
        </v-card>
      </v-content>
    </v-app>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: `Country | ${this.countryName}`,
    };
  },
  data() {
    return {
      countryName: this.$route.params.country,
      countryInfo: [],
    };
  },
  created() {
    this.countryInfo = [];
    this.$axios
      .get(`https://restcountries.eu/rest/v2/name/${this.countryName}`)
      .then((res) => {
        this.countryInfo = res.data;
        // console.log(this.countryInfo[0].capital);
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style></style>
