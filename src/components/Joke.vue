<template>
  <li v-bind:class="{ likedLi: liked }">
    <span>{{ joke.joke }}</span>
    <font-awesome-icon
      class="icon"
      icon="thumbs-up"
      v-bind:class="{ liked: liked }"
      v-on:click="handleLiked"
    />
  </li>
</template>

<script>
export default {
  data() {
    return {
      liked: false,
    };
  },
  methods: {
    handleLiked() {
      if (!this.likedJokes.includes(this.joke.joke)) {
        this.likedJokes.push(this.joke.joke);
        localStorage.liked = this.likedJokes;
        this.liked = !this.liked;
        return
      }

      this.liked = !this.liked;
    },
  },
  mounted() {
      
    if (localStorage.liked.includes(this.joke.joke)) this.liked = true;

  },
  props: {
    joke: {
      type: Object,
      required: true,
    },
    likedJokes: {
      type: Array,
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  justify-content: space-between;
  transition: all 0.4s ease-in;
}

.icon {
  cursor: pointer;
  margin: 3px;
}

.liked {
  color: rgb(163, 73, 247);
}

.likedLi {
  background: rgb(88, 223, 88);
}
</style>
