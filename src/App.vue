<template>
  <Todos />
</template>

<script>
import Todos from "./pages/Todos.vue";

export default {
  name: "App",
  components: {
    Todos,
  },
};
</script>

<style>
* {
  font-family: "Spoqa Han Sans Neo", "sans-serif";
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

html {
  background-color: rgb(234, 231, 222);
}

html,
body {
  height: 100%;
}

#app {
  height: 100%;
  display: flex;
  justify-content: center;
}
</style>
