<template>
  <div class="wrapper">
    <div class="search">
      <input type="text" placeholder="Search" v-model="search" />
      {{ link }}
    </div>
    <div class="about">
      <!-- <Loader/> -->
      <ul v-if="!loading">
        <Joke
          v-for="joke in jokesByTitle"
          v-bind:joke="joke"
          :key="joke.id"
          v-bind:likedJokes="likedJokes"
        />
      </ul>
      <Loader v-else />
    </div>
  </div>
</template>

<script>
import Joke from '@/components/Joke';
import Loader from '@/components/Loader';

export default {
  components: {
    Joke,
    Loader,
  },
  data() {
    return {
      search: '',
      jokes: [],
      loading: true,
      likedJokes: [],
    };
  },
  computed: {
    jokesByTitle() {
      return this.jokes.filter((item) => item.joke.indexOf(this.search) !== -1);
    },
  },
  beforeMount() {
    fetch(
      `https://v2.jokeapi.dev/joke/${this.$route.params.category}?type=single&amount=10`
    )
      .then((response) => response.json())
      .then((json) => {
        if (json.error) return alert('error');
        this.jokes.push(...json.jokes);
        this.loading = false;
      });
  },
};
</script>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  min-width: 200px;
}
.about {
  max-width: 700px;
  width: 60vw;
  height: 80vh;
  min-height: 20vh;
  border: 1px solid black;
  padding: 10px;
  min-width: 200px;
  overflow-y: scroll;
}

.about::-webkit-scrollbar {
  width: 10px;
  background-color: transparent;
}

.about::-webkit-scrollbar-thumb {
  border-radius: 10px;
  background-color: #2de2e2;
}

.about::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.2);
  border-radius: 10px;
  background: transparent;
  outline: none;
}

.search {
  margin-bottom: 10px;
  min-width: 200px;
}

input {
  background: none;
  /* max-width: 400px; */
  min-width: 200px;
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
