<template>
  <div class="card-content-container" :style="{ 'color': color }">
    <h1 class="title"> {{ title }} </h1>
    <p class="description"> {{ description }} </p>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    title: { type: String, default: '' },
    description: { type: String, default: '' },
    color: { type: null, default: 'black' },
  },
};
</script>

<style scoped>
.card-content-container {
  display: none;
  padding: 1em;
}

.title {
  font-size: 2em;
  margin-top: 0;
}

.title, .description {
  text-align: center;
}

.card-content-container.show {
  display: block;
  width: 90%;
  padding: 1em;
}

</style>