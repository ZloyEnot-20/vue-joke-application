<template>
  <div class="about">
    <div class="search">
      <input type="text" placeholder="Search"  v-model="search" />
    </div>

    <!-- <Loader/> -->
    <ul>
      <Joke v-for="joke in jokesByTitle" v-bind:joke="joke" :key="joke.id" />
    </ul>
  </div>
</template>

<script>
import Joke from '@/components/Joke';
import Loader from '@/components/Loader';

export default {
  components: {
    Joke,
    // Loader,
  },
   data() {
    return {
      search: '',
      jokes: [],
    };
  },
  computed: {
    jokesByTitle() {
      return this.jokes.filter(item => item.joke.indexOf(this.search) !== -1)
    },
  },
  beforeMount() {
       fetch('https://v2.jokeapi.dev/joke/Any?type=single&amount=10')
      .then((response) => response.json())
      .then((json) => {
        this.jokes.push(...json.jokes);
       
      });
  },
};
</script>

<style scoped>
.about {
  width: 700px;
  height: auto;
  min-height: 90vh;
  border: 1px solid black;
  padding: 10px;
  margin-bottom: 10px;
}

.search {
  /* display: flex; */
  /* align-items: flex-start; */
}

input {
  background: none;
  width: 400px;
  height: 20px;
  outline: none;
  border: 1px solid black;
}

ul {
  padding: 0;
  margin: 0;
}
li {
  min-height: 40px;
  list-style: none;
  margin: 10px;
  border-radius: 5px;
  padding: 5px;
  border: 1px solid black;
  text-align: left;
}
</style>
