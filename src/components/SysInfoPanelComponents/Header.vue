<template>
  <div id="Header">
    <div class="systemInfo">
      <h3>{{systemName}}</h3>
      <p>{{adress}}</p>
    </div>
    <div class="avrResTime">{{avrResTime + 'ms'}}</div>
  </div>
</template>

<script>
export default {
  props: ['systemName', 'adress', 'avrResTime'],
  name: 'Header',
  components: {},
};
</script>

<style lang="scss" scoped>
#Header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.systemInfo {
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
</style>
