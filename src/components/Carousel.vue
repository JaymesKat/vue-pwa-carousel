<template>
 <div>
  <div class="card-carousel">
    <ArrowButton
      arrowType="left"
      :onClick="showPrevElement"
      :disabled="this.reachedMaxLeft"
    />
   <Card
    class="current-element"
    :headline="currentElement.headline"
    :infoText="currentElement.infoText"
    :imgName="currentElement.imgName"
   />
    <ArrowButton
      arrowType="right"
      :onClick="showNextElement"
      :disabled="this.reachedMaxRight"
    />
  </div>
 </div>
</template>
<script>
import Card from "./Card";
import ArrowButton from "./ArrowButton";
export default {
  name: "Carousel",
  props: { cards: Array },
  components: { Card, ArrowButton },
  data() {
    return {
      currentElementIndex: 0
    };
  },
  computed: {
    currentElement() {
      return this.cards[this.currentElementIndex];
    },
    reachedMaxLeft() {
      return this.currentElementIndex === 0;
    },
    reachedMaxRight() {
      return this.currentElementIndex === this.cards.length - 1;
    }
  },
  methods: {
    showNextElement() {
      this.currentElementIndex++;
    },
    showPrevElement() {
      this.currentElementIndex--;
    }
  }
};
</script>

<style src="../assets/styles/Carousel.css" scoped/>
