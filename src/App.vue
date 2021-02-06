<template>
  <AppHeader/>
  <div class="wrap">
<!--  Сюда подгружаються компоненты  -->
    <router-view></router-view>
  </div>
</template>

<script>
  import AppHeader from "@/components/AppHeader";
  export default {
    components: {
      AppHeader
    },
  }
</script>

<style>

body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.wrap {
  text-align: center;
}
</style>
