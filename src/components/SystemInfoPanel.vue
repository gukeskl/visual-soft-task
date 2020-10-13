<template>
  <div id="system-info-panel" class="info-panel">
    <span v-if="errorMessage">{{errorMessage}}</span>
    <Header
    :SystemName="system.Name"
    :Adress="system.Adress"
    :AvrResTime="system.AvrResTime"
    :AvgResponseTimeAlertLimit="system.AvgResponseTimeAlertLimit"
    :AvgResponseTimeWarningLimit="system.AvgResponseTimeWarningLimit"
    />
    <Charts
      v-if="isDataLoaded"
      :System="system"
      :key="system.LastErrorStr"
      />
    <Footer
      v-if="isDataLoaded"
      :LastError="system.LastErrorStr"
      :LastSyncStr="system.LastSyncStr"
      :DailyErrorCount="system.DailyErrorCount"
      :key="system.LastSyncStr"
    />
  </div>
</template>

<script>
import axios from 'axios';
import Header from './SysInfoPanelComponents/Header.vue';
import Charts from './SysInfoPanelComponents/Charts.vue';
import Footer from './SysInfoPanelComponents/Footer.vue';

export default {
  props: ['URL'],
  name: 'SystemInfoPanel',
  data: () => ({
    system: {
      Name: '',
      Adress: '',
      AvrResTime: '',
      Errors: [],
      Operations: [],
      Warnings: [],
      LastSyncStr: '',
      LastErrorStr: '',
      DailyErrorCount: '',
      AvgResponseTimeAlertLimit: '',
      AvgResponseTimeWarningLimit: '',
    },
    isDataLoaded: false,
    errorMessage: '',
  }),
  components: {
    Header,
    Charts,
    Footer,
  },
  mounted() {
    this.getData();
    setInterval(this.getData, 25000);
  },
  computed: {
  },
  methods: {
    async getData() {
      try {
        const response = await axios.get(this.URL);
        this.system.Name = response.data.Name;
        this.system.Adress = response.data.Url;
        this.system.AvrResTime = response.data.AvgResponseTime;
        this.system.Errors = response.data.Errors;
        this.system.Operations = response.data.Operations;
        this.system.Warnings = response.data.Warnings;
        this.system.LastErrorStr = response.data.LastErrorStr;
        this.system.LastSyncStr = response.data.LastSyncStr;
        this.system.DailyErrorCount = response.data.DailyErrorCount;
        this.system.AvgResponseTimeAlertLimit = response.data.AvgResponseTimeAlertLimit;
        this.system.AvgResponseTimeWarningLimit = response.data.AvgResponseTimeWarningLimit;
        this.isDataLoaded = true;
      } catch (err) {
        this.errorMessage = err;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.info-panel {
  background-color: rgba(0, 0, 0, 0.24);
  padding: 10px 40px 10px 40px;
  box-sizing: border-box;
  max-width: 670px;
  margin: 10px;
}

@media (min-width: 700px) {
  .info-panel {
    max-height: 350px;
  }
}
</style>
