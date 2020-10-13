<template>
  <div id="charts" class="charts-style">
    <div>
      <Chart class="chart-wrapper" :Data="System.Errors" Color="#E23333"/>
      <ImportantValue
      Title="Errors in last hour"
      :MainValue="System.Errors[0].Value"
      :AdditionalValue="errorsAvreage()"
      Color="#E23333"
      />
    </div>
    <div>
      <Chart class="chart-wrapper" :Data="System.Warnings" Color="#CB9B47"/>
      <ImportantValue
      Title="Warnings in last hour"
      :MainValue="System.Warnings[0].Value"
      :AdditionalValue="warningsAvreage()"
      Color="#CB9B47"
      /></div>
    <div>
      <Chart class="chart-wrapper" :Data="System.Operations" Color="#2699FB"/>
      <ImportantValue
      Title="Operations in last hour"
      :MainValue="System.Operations[0].Value"
      Color="#2699FB"
      />
    </div>
  </div>
</template>

<script>
import Chart from './Chart.vue';
import ImportantValue from './ImportantValueComp.vue';

export default {
  props: ['Operations', 'System'],
  name: 'charts',
  components: {
    Chart,
    ImportantValue,
  },
  methods: {
    errorsAvreage() {
      const errorsSum = this.System.Errors.reduce((total, el) => total + el.Value, 0);
      return parseInt(errorsSum / this.System.Errors.length, 10);
    },
    warningsAvreage() {
      const warningsSum = this.System.Warnings.reduce((total, el) => total + el.Value, 0);
      return parseInt(warningsSum / this.System.Warnings.length, 10);
    },
  },
};
</script>

<style lang="scss" scoped>
.chart-wrapper {
  height: 50px;
}

.charts-style > * {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 0px 15px 0px;
}

@media (max-width: 700px) {
  .charts-style > * {
    display: block;
  }
}
</style>
