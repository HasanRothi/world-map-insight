<template>
  <div class="container">
    <img
      style="position: absolute; left: 0px; top: 0px; z-index: -1;"
      src="../assets/images/world_map_PNG17.png"
      height="100%"
      width="100%"
    />
    <v-container fluid>
      <v-row>
        <v-col sm="8" md="8" xs="8" lg="8">
          <v-btn color="rgb(255, 0, 0, 0.01)" to="north america"
            >North America</v-btn
          >
        </v-col>
        <v-col sm="4" md="4" xs="4" lg="4">
          <v-btn color="rgb(255, 0, 0, 0.01)" to="oceania">Oceania</v-btn>
        </v-col>
      </v-row>
      <v-row style="text-align:center">
        <v-col sm="12" md="12" xs="12" lg="12">
          <v-btn color="rgb(255, 0, 0, 0.01)" to="europe">Europe</v-btn>
        </v-col>
      </v-row>
      <v-row style="margin-top:14%;">
        <v-col sm="3" md="3" xs="3" lg="3">
          <v-btn color="rgb(255, 0, 0, 0.01)" to="latin america"
            >Latin America</v-btn
          >
        </v-col>
        <v-col sm="3" md="3" xs="3" lg="3" style="margin-top:10%;">
          <v-btn color="rgb(255, 0, 0, 0.01)" to="africa">Africa </v-btn>
        </v-col>
        <v-col sm="3" md="3" xs="3" lg="3">
          <v-btn color="rgb(255, 0, 0, 0.01)" to="/Middle East"
            >Middle East</v-btn
          >
        </v-col>
        <v-col sm="3" md="3" xs="3" lg="3" style="margin-top:-5%;">
          <v-btn class="white--text" to="/Asia">Asia</v-btn>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "World map insight - Home"
    };
  }
};
</script>
<style></style>
