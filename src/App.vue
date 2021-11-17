<template>
  <div id="app">
    <div
      class="server-row"
      v-for="row in 3"
      :key="row"
    >
      <ServerStatus
        v-for="index in range((row-1)*7+1, row*7)"
        :key="index"
        :id="index < 20 ? index : -1"
      />
    </div>
  </div>
</template>

<script>
import ServerStatus from './components/ServerStatus.vue'

export default {
  name: 'App',
  components: {
    ServerStatus
  },
  methods: {
    range : function (start, end) {
      return Array(end - start + 1).fill().map((_, idx) => start + idx)
   }
  }
}
</script>

<style lang="scss">
html, body {
  background-color: black;
  height: 100%;
  margin: 0;
  overflow: hidden;
}

body {
  margin: 0 90px;
}

#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 100%;

  // font-family: Avenir, Helvetica, Arial, sans-serif;
  font-family: consolas;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: white;
}

.server-row {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin: 18px 0;
}
</style>
