<template>
  <div id="app">
    <CountDown title="論文提出日" :due-time="new Date(2019, 0, 16)" class="timer" />
  </div>
</template>

<script>
import CountDown from './components/CountDown'

export default {
  name: 'App',
  components: {
    CountDown
  }
}
</script>

<style>
body {
  margin: 0;
  height: 100vh;
  background-color: #2c3e50;
}

#app {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
