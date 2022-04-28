<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style lang="scss">
@import "@/assets/style/helper.scss";
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  line-height: 1.5;
  font-family: $font-hei;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #333;
  font-size: 16px;
  background: #f5f5f5;
}
a {
  text-decoration: none;
  color: inherit;
}
ul,
ol {
  list-style: none;
}
button,
input {
  font: inherit;
}
:focus {
  outline: none;
}
</style>
