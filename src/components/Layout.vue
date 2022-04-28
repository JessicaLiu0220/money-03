<template>
  <div class="nav-wrapp">
    <div class="concern" :class="classPrefix && `${classPrefix}-concern`">
      <slot />
    </div>
    <Nav />
  </div>
</template>

<script lang='ts'>
export default {
  props: ["classPrefix"],
};
</script>

<style lang="scss" scoped>
.nav-wrapp {
  display: flex;
  flex-direction: column;
  height: 100vh;
}
.concern {
  overflow: auto;
  flex-grow: 1;
}
</style>