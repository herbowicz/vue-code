<template>
  <div class="container">

    <section class="section">
      <div class="container">
        <h1 class="title">
          code.wroclaw.pl
        </h1>
        <p class="subtitle">
          Built with <strong>Vue.js</strong> & <strong>Bulma</strong>
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
     font-size: 2.5em;
  }
</style>
