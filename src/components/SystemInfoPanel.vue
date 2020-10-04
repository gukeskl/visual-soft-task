<template>
  <div id="SystemInfoPanel">
    <Header :systemName="system.name" :adress="system.adress" :avrResTime="system.avrResTime"/>
    <Charts :Errors="system.Errors" :key="system.Errors.length"/>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './SysInfoPanelComponents/Header.vue';
import Charts from './SysInfoPanelComponents/Charts.vue';

export default {
  name: 'SystemInfoPanel',
  data: () => ({
    system: {
      name: '',
      adress: '',
      avrResTime: '',
      Errors: [],
      Operations: [],
      Warnings: [],
    },
  }),
  components: {
    Header,
    Charts,
  },
  mounted() {
    this.getData();
    setInterval(this.getData, 20000);
  },
  computed: {
  },
  methods: {
    async getData() {
      const response = await axios.get('https://visualsoft.com.pl/rekrutacja/202009/dane');
      console.log(response);
      this.system.name = response.data.Name;
      this.system.adress = response.data.Url;
      this.system.avrResTime = response.data.AvgResponseTime;
      this.system.Errors = response.data.Errors;
      this.system.Operations = response.data.Operations;
      this.system.Warnings = response.data.Warnings;
    },
  },
};
</script>

<style lang="scss" scoped>
#SystemInfoPanel {
  background-color: rgba(0, 0, 0, 0.24);
  max-width: 700px;
  padding: 10px 40px 10px 40px;
}
</style>
