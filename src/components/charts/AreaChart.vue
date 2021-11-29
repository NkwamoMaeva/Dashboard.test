<script>
import { Line, Bar } from "vue-chartjs";
import axios from "axios";

export default {
  extends: Bar,
  Line,
  props: ["city"],
  data() {
    return {
      dates: [],
      temps: [],
      tempMax: [],
      humidities: [],
      loading: false,
      gradient: null,
    };
  },
  mounted() {
    // Define gradient color
    this.gradient = this.$refs.canvas
      .getContext("2d")
      .createLinearGradient(0, 0, 0, 450);

    this.gradient.addColorStop(0.5, "rgba(0, 231, 255, 0.1)");
    this.gradient.addColorStop(1, "rgba(0, 231, 255, 0)");

    this.getData();
  },
  methods: {
    getData() {
      // Get data from API using Axios
      axios
        .get("https://api.openweathermap.org/data/2.5/forecast", {
          params: {
            q: this.city,
            units: "imperial",
            appid: "fd3150a661c1ddc90d3aefdec0400de4",
          },
        })
        .then((response) => {
          this.dates = response.data.list.map((list) => {
            return list.dt_txt;
          });

          this.temps = response.data.list.map((list) => {
            return list.main.temp;
          });

          this.tempMax = response.data.list.map((list) => {
            return list.main.feels_like;
          });

          this.humidities = response.data.list.map((list) => {
            return list.main.humidity;
          });

          // Render Chart
          this.renderChart(
            {
              labels: this.dates,
              datasets: [
                {
                  type: "line",
                  label: "Degrée max",
                  backgroundColor: "transparent",
                  borderColor: "#FF8373",
                  pointBackgroundColor: "white",
                  data: this.tempMax,
                  yAxisID: "A",
                },
                {
                  type: "line",
                  label: "Degrée",
                  backgroundColor: this.gradient,
                  borderColor: "#05CBE1",
                  pointBackgroundColor: "white",
                  data: this.temps,
                  yAxisID: "A",
                },
                {
                  showLine: false,
                  type: "bar",
                  label: "Humidité",
                  data: this.humidities,
                  yAxisID: "B",
                  borderRadius: 5,
                },
              ],
            },

            //Chart Options
            {
              responsive: true,
              maintainAspectRatio: false,
              scales: {
                xAxes: [
                  {
                    type: "time",
                    time: {
                      unit: "hour",
                      displayFormats: {
                        hour: "DD/M-hA",
                      },
                      tooltipFormat: "MMM. DD @ hA",
                    },
                  },
                ],
                yAxes: [
                  {
                    id: "A",
                    position: "left",
                    ticks: {
                      callback: function (value) {
                        return value + "°F";
                      },
                    },
                  },
                  {
                    id: "B",
                    position: "right",
                    gridLines: {
                      color: "rgba(0, 0, 0, 0)",
                    },
                  },
                ],
              },
              legend: {
                labels: {
                  usePointStyle: true,
                },
                display: true,
                position: "top",
                align: "left",
              },
              tooltips: {
                callbacks: {
                  label: function (tooltipItem, data) {
                    var label =
                      data.datasets[tooltipItem.datasetIndex].label || "";

                    if (label) {
                      label += ": ";
                    }

                    label += Math.floor(tooltipItem.yLabel);
                    return label + "°F";
                  },
                },
              },
            }
          );
        })
        .catch((error) => {
          console.log(error);
          this.errored = true;
        })
        .finally(() => (this.loading = false));
    },
  },
};
</script>
