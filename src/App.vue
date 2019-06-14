<template>
  <div id="app">
    <ContactForm msg="This is my contact form" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import ContactForm from "./components/ContactForm";

export default {
  name: "app",
  components: {
    HelloWorld,
    ContactForm
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
