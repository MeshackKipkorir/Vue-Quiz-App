<template>
  <div id="app">
    <Quiz />
    <footer>
      <p id="createdBy">
        created by <a href="mailto:meshackkipkorir105@gmail.com">Meshack Kipkorir</a>
      </p>
    </footer>
  </div>
</template>

<script>
import Quiz from "@/components/Main.vue";
 
export default {
  name: "App",
  components: {
    Quiz,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
}
#app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica,
    Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
footer {
  position: fixed;
  bottom: 0;
  padding: 0.5rem 1rem;
  width: 100%;
  font-size: 0.7rem;
}
#createdBy {
  float: right;
}
</style>