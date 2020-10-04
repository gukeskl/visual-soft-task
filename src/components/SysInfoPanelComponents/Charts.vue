<template>
  <div id="Charts">
      <Chart :Data="Errors"/>
  </div>
</template>

<script>
import Chart from './Chart.vue';

export default {
  props: ['Errors', 'Operations', 'Warnings'],
  name: 'Charts',
  components: {
    Chart,
  },
};
</script>

<style lang="scss" scoped></style>
