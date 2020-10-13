<template>
  <div id="important-value-comp" class="important-value" :style="{ color: Color}">
      <div class="main-value">{{MainValue}}</div>
      <div class="additional-value"
           v-if="AdditionalValue"
           :style="{ color: Color + '67'}">
           ({{AdditionalValue}})
      </div>
      <div>{{Title}}</div>
  </div>
</template>

<script>
export default {
  props: ['Title', 'MainValue', 'AdditionalValue', 'Color'],
  name: 'important-value-comp',
  components: {
  },
};
</script>

<style lang="scss" scoped>
.important-value {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-size: 11px;
    min-width: 120px;
}
.main-value{
    font-size: 25px;
}
.additional-value {
    font-size: 15px;
    //opacity: 0.67;
}
</style>
