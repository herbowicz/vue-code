<template>
  <div class="container">

    <section class="section">
      <div class="container">
        <h1 class="title">
          code.wroclaw.pl
        </h1>
        <p class="subtitle">
          Built with <a href="https://vuejs.org/">Vue.js</a> & <a href="https://bulma.io/">Bulma</a>
        </p>
      </div>
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
     font-size: 3em;
  }
  .subtitle {
    color: hsla(0, 0%, 0%, 0.35);
  }
  .subtitle a {
    text-decoration: none;
    color: hsla(0, 0%, 0%, 0.45);
  }
</style>
