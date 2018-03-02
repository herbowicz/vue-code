<template>
  <div class="container">

    <section class="section">
      <h1 class="title">
        code.wroclaw.pl
      </h1>
      <p class="subtitle">
        GitHub API v3 Ajax call with <a href="https://bulma.io/">Bulma</a> & <a href="https://vuejs.org/">Vue.js</a>
      </p>
    </section>

    <Coders />
  </div>
</template>

<script>
import 'bulma/css/bulma.css'
import Coders from './Coders'

export default {
  name: 'Container',
  components: {
    Coders
  }
}
</script>

<style scoped>
  h1 {
   color: #008000;
   font-size: 4em;
   font-weight: 400;
  }
  .subtitle {
    color: hsla(0, 0%, 0%, 0.35);
  }
  .subtitle a {
    text-decoration: none;
    color: #008000;
  }
</style>
