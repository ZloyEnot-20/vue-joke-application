<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/jokes">Jokes</router-link>
      
    </div>
    <router-view v-bind:jokes="jokes" />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}

#nav {
  padding: 30px;
  display: flex;
  align-items: center;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>

<script>
export default {
  data() {
    return {
      jokes: [],
    };
  },
  mounted() {
    fetch('https://v2.jokeapi.dev/joke/Any?type=single&amount=10')
      .then((response) => response.json())
      .then((json) => {
        this.jokes.push(...json.jokes)
        console.log(json);
      });
  },
};
</script>
