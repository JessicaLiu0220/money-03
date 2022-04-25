<template>
  <div class="nav">
    <router-link to="/money" class="item" active-class="slected">
      <Icon name="money" />
      <div class="slectedcolor">记账</div>
    </router-link>
    <router-link to="/labels" class="item" active-class="slected">
      <Icon name="label" />
      <div class="slectedcolor">标签</div>
    </router-link>
    <router-link to="/statistics" class="item" active-class="slected">
      <Icon name="statistics" />
      <div class="slectedcolor">统计</div>
    </router-link>
  </div>
</template>

<script lang="ts">
export default {};
</script>

<style lang="scss" scoped>
@import "@/assets/style/helper.scss";

.nav {
  @extend %outerShadow;
  display: flex;
  flex-direction: row;
  font-size: 12px;
  > .item {
    padding: 2px 0;
    width: 33.33333%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    .icon {
      width: 32px;
      height: 32px;
    }
  }
  > .slected {
      color: $color-highlight;
  }
}
</style>