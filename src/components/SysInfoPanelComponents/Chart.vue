<script>
import { Bar } from 'vue-chartjs';

export default {
  name: 'Chart',
  extends: Bar,
  props: ['Data', 'Color'],

  data: () => ({
    options: {
      legend: false,
      responsive: true,
      maintainAspectRatio: false,
      scales: {
        xAxes: [
          {
            stacked: true,
            ticks: {
              fontColor: '',
              defaultFontSize: 7,
              autoSkip: true,
              maxRotation: 0,
              minRotation: 0,
            },
            gridLines: {
              display: false,
            },
          },
        ],
        yAxes: [
          {
            gridLines: {
              display: false,
            },
            ticks: {
              suggestedMin: 0,
              display: false,
            },
          },
        ],
      },
    },
    dataset: {
      labels: [],
      datasets: [
        {
          barPercentage: 0.5,
          data: [],
          backgroundColor: '',
        },
      ],
    },
  }),
  computed: {
  },
  mounted() {
    this.Data.forEach((el, index, arr) => {
      if (arr.length - 40 <= index) {
        const hour = new Date(el.Date).getHours();
        this.dataset.datasets[0].data.unshift(el.Value);
        if (hour % 2 === 0) this.dataset.labels.unshift(`${hour}`);
        else this.dataset.labels.unshift('');
      }
    });
    this.options.scales.xAxes[0].ticks.fontColor = this.Color;
    this.dataset.datasets[0].backgroundColor = this.Color;
    this.renderChart(this.dataset, this.options);
  },
};
</script>
