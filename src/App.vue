<template>
  <AppHeader/>
  <div class="wrap">
<!--    <DcHeros/>-->
    <Calendar/>
  </div>
</template>

<script>
  import AppHeader from "@/components/AppHeader";
  import Calendar from "@/components/Calendar";
  // import DcHeros from "@/components/DcHeros";
  export default {
    components: {
      Calendar,
      // DcHeros,
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
