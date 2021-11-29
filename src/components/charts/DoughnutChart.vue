<script>
import { Doughnut } from "vue-chartjs";

export default {
  extends: Doughnut,
  data() {
    return {
      sales: [],
    };
  },
  mounted() {
    this.getData();
    this.renderChart(
      {
        labels: ["France", "Italie", "Espagne", "Allemagne", "Canada"],
        datasets: [
          {
            backgroundColor: [
              "#A3A0FB",
              "#55D8FE",
              "#00D8FF",
              "#FF8373",
              "#FFDA83",
            ],
            pointBackgroundColor: "white",
            data: this.sales,
          },
        ],
      },
      {
        responsive: true,
        maintainAspectRatio: false,
        legend: {
          display: true,
          position: "right",
          labels: {
            usePointStyle: true,
          },
        },
        cutoutPercentage: 60,
      }
    );
  },
  methods: {
    // Generate data
    getData(){
      this.sales=[];
      for(let i=0; i<5; i++){
        let random = Math.floor(Math.random()*100000)
        this.sales.push(random)
      }
      console.log(this.sales);
    },
    plugin(chart) {
      const { width, height, ctx } = chart.chart;
      ctx.restore();
      const fontSize = (height / 150).toFixed(2);
      ctx.font = `${fontSize}rem sans-serif`;
      ctx.textBaseline = "middle";
      var sum = this.sales.reduce(function (pv, cv) {
        return pv + cv;
      }, 0);

      const text = sum;
      const textX = Math.round((width - ctx.measureText(text).width) / 2);
      const textY = height / 2;

      ctx.fillText(text, textX, textY);
      ctx.save();
    },
  },
};
</script>
