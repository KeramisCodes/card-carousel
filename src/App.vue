<template>
  <main>
    <div class="heading">
      <h1>Study Cards</h1>
      <p><b>Instructions</b>: Use the cards below to study.</p>
    </div>
      <CardCarousel 
      arrowBkgColor="#3e968c"
      bkgColor="#fdfdfd"
      >
        <Card 
          title="Title 1" 
          description="Description 1"
          color="#4c4d4c"
        />

        <Card 
          title="Title 2" 
          description="Description 2"
          color="#4c4d4c"
        />
        
        <Card 
          title="Title 3" 
          description="Description 3"
          color="#4c4d4c"
        />
    </CardCarousel>
  </main>
  
</template>


<style scoped>
  .heading {
    text-align: center;
  }
</style>


<script>
import CardCarousel from './components/card-component.vue'
import Card from './components/card-content.vue'
export default {
  components: {
    CardCarousel,
    Card,
  },
};
</script>