<template>
  <div id="header" class="header-wrapper">
    <div class="system-info">
      <h3>{{SystemName}}</h3>
      <p>{{Adress}}</p>
    </div>
    <ImportantValue
    Title="Average response time"
    :MainValue="`${AvrResTime}ms`"
    :Color="valueColor"
    />
  </div>
</template>

<script>
import ImportantValue from './ImportantValueComp.vue';

export default {
  props: ['SystemName', 'Adress', 'AvrResTime', 'AvgResponseTimeAlertLimit', 'AvgResponseTimeWarningLimit'],
  name: 'Header',
  components: {
    ImportantValue,
  },
  computed: {
    valueColor() {
      let color = '#777780';
      if (parseInt(this.AvrResTime, 10) > parseInt(this.AvgResponseTimeWarningLimit, 10)) color = '#CB9B47';
      if (parseInt(this.AvrResTime, 10) > parseInt(this.AvgResponseTimeAlertLimit, 10)) color = '#E23333';
      return color;
    },
  },
};
</script>

<style lang="scss" scoped>
.header-wrapper {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding-left: 10px;
}

.system-info {
  h3,
  p {
    margin: 0px;
  }
  p {
    color: #777780;
    font-size: 14px;
  }
  h3 {
    font-size: 33px;
    font-weight: normal;
  }
}

@media (min-width: 700px) {
  .header-wrapper {
    flex-direction: row;
  }
}

@media (max-width: 700px) {
  .header-wrapper {
    flex-direction: column;
    margin-bottom: 10px;
  }
  .system-info{
    display: flex;
    flex-direction: column;
    align-items: center;
    & h3 {
      text-align: center;
    }
    margin-bottom: 10px;
  }

}
</style>
