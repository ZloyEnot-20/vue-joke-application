<template>
  <div class="home">
    <h3>What kind of jokes you like?</h3>
    <router-link
      class="link"
      :to="{ name: 'Jokes', params: { category: category } }"
      v-for="category of jokeCategories"
      :key="category"
      >{{ category }}</router-link
    >
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
// import Loader from '@/components/Loader';

@Component({
  components: {},
})
export default class Home extends Vue {
  data() {
    return {
      jokeCategories: [
        'Any',
        'Programming',
        'Miscellaneous',
        'Dark',
        
      ]
    };
  }
}
</script>

<style scoped>
.home {
  width: 400px;
  height: 100vh;
  border: 1px solid black;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.link {
  display: inline-block;
  outline: none;
  color: black;
  text-decoration: none;
  width: 220px;
  font-size: 1.5rem;
  margin-bottom: 5px;
  border-radius: 5px;
  transition: all 0.3s ease-in;
  background-color: #40c90a;
}

.link:hover {
  opacity: 0.6;
}
</style>
