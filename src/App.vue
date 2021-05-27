<template>
  <div id="app">
    <div id="nav"></div>
    <router-view />
  </div>
</template>
<script>
export default {
  
};
</script>
<style lang="scss">
* {
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  -webkit-tap-highlight-color: transparent;
  padding: 0;
  margin: 0;
}
select {
  appearance: none;
  -moz-appearance: none;
  background: #ffffff;
  -webkit-appearance: none;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  -webkit-tap-highlight-color: transparent;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  // padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
