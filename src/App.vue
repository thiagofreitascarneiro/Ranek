<template>
  <div id="app">
    <TheHeader />
    <router-view/>
    <TheFooter />
  </div>
</template>

<script>

import TheHeader from "@/components/TheHeader.vue";
import TheFooter from "@/components/TheFooter.vue";

export default {
  components: {
    TheHeader,
    TheFooter
  }
  
}
</script>

<style>
body, ul, li, h1, h2, p {
  padding: 0px;
  margin: 0 auto;
}

ul {
  list-style: none;
}

body {
  font-family: "Arial", Helvetica, sans-serif;
  color: #345;
  background: url('./assets/pattern.svg') repeat top;
}

</style>
