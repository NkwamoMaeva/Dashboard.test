<script>
import { Bar } from "vue-chartjs";

export default {
  extends: Bar,
  mounted() {
    // Render Chart
    this.renderChart(
      {
        labels: [
          "January",
          "February",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December",
        ],
        datasets: [
          // Define Data
          {
            label: "Chat",
            backgroundColor: "#f87979",
            data: [40, 20, 12, 39, 10, 40, 39, 80, 40, 20, 12, 11],
          },
          {
            label: "Chien",
            backgroundColor: "#05CBE1",
            data: [15, 56, 18, 20, 12, 32, 45, 58, 40, 24, 47, 35],
          },
        ],
      },
      {
        responsive: true,
        maintainAspectRatio: false,
        legend: {
          display: true,
          position: "top",
          align: "center",
          labels: {
            usePointStyle: true,
          },
        },
      }
    );
  },
};
</script>
