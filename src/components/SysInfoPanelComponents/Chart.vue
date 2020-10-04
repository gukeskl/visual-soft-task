<script>
import { Bar } from 'vue-chartjs';

export default {
  name: 'Chart',
  extends: Bar,
  props: ['Data'],

  data: () => ({
    options: {
      legend: false,
      responsive: false,
      maintainAspectRatio: false,
      scales: {
        xAxes: [
          {
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
          label: 'Blue',
          data: [],
          backgroundColor: '#f87979',
        },
      ],
    },
  }),
  computed: {
  },
  mounted() {
    this.Data.forEach((el, index) => {
      this.dataset.datasets[0].data.push(el.Value);
      if (index % 2 === 0) this.dataset.labels.push(`${el.Value}`);
      else this.dataset.labels.push('');
    });
    this.renderChart(this.dataset, this.options);
  },
};
</script>

<style lang="scss" scoped>
.color-test {
  background-color: rgba(0, 247, 111, 1);
}
</style>
