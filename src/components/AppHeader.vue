<template>
  <nav>
    <router-link
        v-for="item in list"
        :key="item.to"
        :to="item.to">
      {{ item.title }}
    </router-link>
  </nav>
</template>

<script>
export default {
  name: "AppHeader",
  data() {
    return {
      list: [
        {
          title: "Dc heros",
          to: "/ds-heros"
        },
        {
          title: "Calendar",
          to: "/calendar"
        },
        {
          title: "Markdown",
          to: "/markdown"
        }
      ]
    }
  }
}
</script>

<style scoped>
  nav {
    background-color: blueviolet;
    color: aliceblue;
    font-weight: bold;
  }
  nav a {
    padding: 5px;
    color: #fff;
    text-decoration: none;
  }
</style>