<template>
  <div id="app">
    <SystemInfoPanel />
  </div>
</template>

<script>
import SystemInfoPanel from './components/SystemInfoPanel.vue';

export default {
  name: 'App',
  components: {
    SystemInfoPanel,
  },
};
</script>

<style lang="scss">
body{
    margin: 0;

}
#app{
    min-height: 100vh;
    width: 100vw;
    box-sizing: border-box;
    padding: 20px;
    background: linear-gradient(0deg, rgba(9,12,21,1) 0%, rgba(100,113,112,1) 100%);
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #FFFFFF;
}
</style>
