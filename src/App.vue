<template>
  <div id="app">
    <img class="rounded-circle" src="./assets/1.jpg" width="20%" />
    <HelloWorld msg="Cs313_Game" />
    <h6 class="text-light">สุ่มตัวละครต่อสู้กันเถอะ!</h6>
    <br>
    <div>
      <botton />
    </div>
    <footer class="my-0 pt-0 text-muted text-center text-small">
        <p class="mb-0">&copy; cs313@6104101352</p>
    </footer>
  </div>
</template>
<script>
import HelloWorld from "./components/HelloWorld.vue";
import botton from "./components/botton.vue";
export default {
  name: "App",
  components: {
    HelloWorld,
    botton,
  },
};
</script>
<style>
#app {
  background-image: url(https://cdn.pixabay.com/photo/2015/06/30/22/52/gradient-826969_960_720.jpg);
  height: 100%;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  position: relative;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000;
}

</style>
