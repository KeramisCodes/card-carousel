<template>
  <div class="card-main">
    <div class="card-container" :style="{ 'backgroundColor': bkgColor }" :index="index">

      <form class="arrow-container" :style="{ 'backgroundColor': arrowBkgColor}" @submit.prevent="moveLeft">
        <div class="left-arrow">
          <input class="arrow" type="image" src="/src/assets/img/caret-left-solid.svg" alt="Left Arrow">
        </div>
      </form>

      <div class="card-content">
        <slot :id="this.id"></slot>
      </div>

      <form class="arrow-container" :style="{ 'backgroundColor': arrowBkgColor}" @submit.prevent="moveRight">
        <div class="rightArrow">
          <input class="arrow" type="image" src="src/assets/img/caret-right-solid.svg" alt="Right Arrow">
        </div>
      </form>

    </div>
  </div>

</template>


<style scoped>
.card-main {
  min-width: 250px;
  max-width: 300px;
  margin-left: auto;
  margin-right: auto;
  padding: 2em;
}

.card-container {
  display: flex;
  width: 100%;
  min-height: 150px;
  border-radius: 15px;
  border: solid 1px black;
  overflow: hidden;
}

.card-content {
  width: 90%;
  padding: 1em;
}

.arrow-container {
  display: grid;
  place-items: center;
  width: 10%;
}

.left-arrow, .right-arrow {
  display: grid;
  place-items: center;
  width: 100%;
}

.arrow {
  width: 60%;
}

.arrow:hover {
  filter: invert(99%) sepia(100%) saturate(2%) hue-rotate(40deg) brightness(106%) contrast(100%);
}
</style>


<script>
import Card from './card-content.vue'
export default {
  name: 'CardCarousel',
  components: {
    Card,
  },
  props: {
    arrowBkgColor: { type: null, default: ''},
    bkgColor: { type: null, default: ''},
  },
  data() {
    return {
      id: 0,
      index: 1,
      allCards: [],
    };
  },
  mounted(){
    this.setCardId();
    this.getCards();
    this.isActive();
  },
  methods: {
    setCardId(){
      const cards = document.querySelectorAll('.card-content-container');
      cards.forEach((card) => {
        this.id++;
        card.id = this.id;
      });
      this.id = 0;
    },
    getCards(){
      const cards = document.querySelectorAll('.card-content-container');
      cards.forEach((card) => {
        this.allCards.push(card); 
      });
    },
    isActive() {
      const activeCard = document.querySelectorAll('.card-content-container');
      activeCard.forEach((active) => {
        if(active.id == this.index)
          active.classList.add('show');
        else active.classList.remove('show');
      });
    },
    moveLeft() {
      if(this.index > 1) {
        this.index = this.index -1;
        this.isActive();
      };
    },
    moveRight() {
      if(this.index < this.allCards.length) {
        this.index = this.index + 1;
        this.isActive();
      };
    },
  },
}
</script>