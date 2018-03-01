<template>
  <div id="app">
    <header>
      <img src="./assets/logo.png" alt="code logo">
    </header>
    <main>
      <router-view></router-view>
    </main>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

main {
  text-align: center;
}

header img {
  width: 50px;
  height: 50px;
}

header {
  margin: 0;
  height: 50px;
  padding: 0 20px;
  background-color: #dedecf;
  color: #ffffff;
}
</style>
