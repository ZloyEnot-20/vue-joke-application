<template>
  <li>{{joke.joke}}</li>
</template>

<script>
export default {
  props: {
      joke:{
          type: Object,
          required: true
      }
  }
};
</script>
