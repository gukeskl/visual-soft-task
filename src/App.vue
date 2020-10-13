<template>
  <div id="app" class="app-wrapper">
    <SystemInfoPanel v-for="URL in URLs" :URL="URL" :key="URL" />
  </div>
</template>

<script>
import SystemInfoPanel from './components/SystemInfoPanel.vue';

export default {
  name: 'App',
  components: {
    SystemInfoPanel,
  },
  data: () => ({
    URLs: [
      'https://visualsoft.com.pl/rekrutacja/202009/dane',
      'https://visualsoft.com.pl/rekrutacja/202009/dane',
      'https://visualsoft.com.pl/rekrutacja/202009/dane',
    ],
  }),
};
</script>

<style lang="scss">
body {
  margin: 0;
}

.app-wrapper {
  min-height: 100vh;
  width: 100vw;
  box-sizing: border-box;
  padding: 20px;
  background: linear-gradient(0deg, rgba(9, 12, 21, 1) 0%, rgba(100, 113, 112, 1) 100%);
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #ffffff;
}

@media (min-width: 700px) {
  .app-wrapper {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    box-sizing: border-box;
  }
}
</style>
