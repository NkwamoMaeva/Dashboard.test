<template>
  <v-app>
    <NavBar />
    <v-main class="container">
      <Drawer />
      <div class="sub-container">
        <span class="text-h4 title"> Overview </span>
        <div class="chart area-chart">
          <div class="d-flex flex-row justify-space-between align-center mb-4">
            <span class="text-subtitle-1"> Trends statistics </span>
            <v-select
              class="city-select text-subtitle-1"
              :items="cities"
              v-model="city"
              dense
              outlined
              hide-details
              @change="$refs.firstChart.getData()"
            ></v-select>
          </div>
          <AreaChart ref="firstChart" :city="city" style="height: 300px" />
        </div>
        <div class="chart chart-1">
          <div class="d-flex flex-row justify-space-between align-center mb-4">
            <span class="text-subtitle-1"> Distributions </span>
          </div>
          <DoughnutChart style="height: 240px" />
        </div>
        <div class="chart chart-2">
          <div class="d-flex flex-row justify-space-between align-center mb-4">
            <span class="text-subtitle-1"> Statistics </span>
          </div>
          <BarChart :city="city" style="height: 300px" />
        </div>
        <div class="chart chart-3">
          <div class="d-flex flex-row justify-space-between align-center mb-4">
            <span class="text-subtitle-1"> Money </span>
          </div>
          <MoneyChart />
        </div>
        <div class="chart chart-4">
          <RadarChart />
        </div>
      </div>
    </v-main>
  </v-app>
</template>

<script>
import NavBar from "./components/NavBar";
import Drawer from "./components/menus/Drawer";
import AreaChart from "./components/charts/AreaChart";
import BarChart from "./components/charts/BarChart";
import MoneyChart from "./components/charts/MoneyChart";
import RadarChart from "./components/charts/RadarChart";
import DoughnutChart from "./components/charts/DoughnutChart.vue";

export default {
  name: "App",

  components: {
    NavBar,
    Drawer,
    AreaChart,
    BarChart,
    DoughnutChart,
    MoneyChart,
    RadarChart
  },

  data: () => ({
    toggle_exclusive: undefined,
    cities: ["Lyon", "Bordeaux", "Lille", "Paris", "Marseille"],
    countries: ["Europe", "Amerique", "Afrique", "Océanie", "Asie"],
    country: "Europe",
    city: "Lyon",
  }),
};
</script>
<style lang="scss" scoped>
.container {
  background-color: #f0f0f7;
  .sub-container {
    padding: 20px 50px 0 100px;
    overflow-x: scroll;
    display: grid;
    column-gap: 10px;
    row-gap: 10px;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    grid-template-rows: auto;
    grid-template-areas:
      "title title title title"
      "area-chart area-chart area-chart area-chart"
      "chart-1 chart-2 chart-2 chart-2"
      "chart-3 chart-3 chart-4 chart-4"
      "chart-5 chart-6 chart-6 chart-6"
      "chart-7 chart-8 chart-8 chart-8";

    .chart {
      background-color: white;
      box-shadow: 0px 0px 9px -7px #000000;
      border-radius: 2px;
      padding: 12px;
    }
    .title {
      grid-area: title;
    }
    .area-chart {
      grid-area: area-chart;
    }
    .chart-1 {
      grid-area: chart-1;
    }
    .chart-2 {
      grid-area: chart-2;
    }
    .chart-3 {
      grid-area: chart-3;
    }
    .chart-4 {
      grid-area: chart-4;
    }
  }
}
.city-select {
  max-width: 150px;
  .v-input__control {
    min-height: 32px !important;
  }
}
.area-chart {
  #bar-chart {
    height: 200px;
  }
}
.chart-2 {
  #bar-chart {
    height: 200px;
  }
}
</style>
