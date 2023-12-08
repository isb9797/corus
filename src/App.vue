<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>


<!--      <nav>-->
<!--        <RouterLink to="/">Home</RouterLink>-->
<!--        <RouterLink to="/about">About</RouterLink>-->
<!--      </nav>-->


  <RouterView />
</template>

<style  lang="sass">
*
  padding: 0
  margin: 0
  box-sizing: border-box

@font-face
  font-family: "FactorA-Regular"
  font-weight: 400
  font-style: normal
  font-display: auto
  src: local("FactorA-Regular"), url("/fonts/FactorA-Regular.woff2") format("woff2"), url("/fonts/FactorA-Regular.woff") format("woff")


body
  font-family: FactorA-Regular



</style>
