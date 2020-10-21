<template>
  <div id="app">
    <the-header title="Remember Me"></the-header>
    <the-resources></the-resources>
  </div>
</template>

<script>
import TheHeader from "@/components/Layouts/TheHeader";
import TheResources from "@/components/LearnResources/TheResources";

export default {
  name: 'App',
  components: {
    TheHeader,
    TheResources
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}
html {
  font-family: 'Roboto', sans-serif;
}
body {
  margin: 0;
}
</style>
