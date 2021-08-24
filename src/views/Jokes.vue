<template>
  <div class="about">
    <Loader/>
    <ul>
      <Joke v-for="joke of jokes" v-bind:joke="joke" v-bind:key="joke.id" />
    </ul>
  </div>
</template>

<script>
import Joke from '@/components/Joke';
import Loader from '@/components/Loader';

export default {
  props: ['jokes'],
  components: {
    Joke,
    Loader,
  },
};
</script>

<style scoped>
.about {
  width: 700px;
  height: auto;
  border: 1px solid black;
}
ul {
  padding: 0;
  margin: 0;
}
li {
  list-style: none;
  margin: 10px;
  padding: 5px;
  border: 1px solid black;
  text-align: left;
}
</style>
