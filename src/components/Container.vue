<template>
  <div class="container">

    <section class="section">
      <div class="container">
        <h1 class="title">
          code.wroclaw.pl
        </h1>
        <p class="subtitle">
          Built with <strong>Vue.js</strong> & <strong>Bulma</strong>!
        </p>
      </div>
    </section>

    <Coders />

    <progress class="progress" value="5" max="100">15%</progress>

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
