<template>
  <section id="app">
    <Header />
  </section>
</template>

<script>
import Header from './components/Header'

export default {
  name: 'app',
  components: {
    Header
  }
}
</script>

<style>
body,
#slider,
.header,
.slide-content {
  margin: 0;
  padding: 0;
  font-family: 'Montserrat', sans-serif;
  width: 100%;
  height: 100vh;
  overflow-x: hidden;
}
</style>
