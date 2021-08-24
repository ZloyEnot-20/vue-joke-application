<template>
  <li>
    <span>{{ joke.joke }}</span> <font-awesome-icon class="icon" icon="thumbs-up" />
  </li>
</template>

<script>
export default {
  props: {
    joke: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
li{
    display: flex;
    justify-content: space-between;

}

.icon{
    cursor: pointer;
    margin: 3px;
}
</style>
