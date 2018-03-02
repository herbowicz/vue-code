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
@import url('https://fonts.googleapis.com/css?family=VT323');
body {
  margin: 0;
}

#app {
  font-family: 'VT323', monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #008000;
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
  border-top: 2px solid #008000;
  height: 50px;
  padding: 0 20px;
  background-color: #dedecf;
  color: #ffffff;
}
</style>
