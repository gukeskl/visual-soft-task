<template>
  <div id="Footer" class="footer-style">
      <span>LastError: {{LastError}}</span>
      <span>Since last sync: {{TimeLeftSinceLastSync}}</span>
      <span>Daily error count: {{DailyErrorCount}}</span>
  </div>
</template>

<script>
import moment from 'moment';

export default {
  props: ['LastError', 'LastSyncStr', 'DailyErrorCount'],
  name: 'Footer',
  computed: {
    TimeLeftSinceLastSync() {
      return moment(this.LastSyncStr).fromNow();
    },
  },
};
</script>

<style lang="scss" scoped>
.footer-style {
    display: flex;
    justify-content: space-between;
    color: #8E8EC1;
    font-size: 11px;
    padding-left: 10px;
    padding-right: 5px;

    & > * {
        margin: 5px;
    }
}
</style>
