<template>
  <div class="output-section">
    <h1 class="title-margin">Nutrition Analysis</h1>
    <div class="results-section">
      <p>Fruit Name: {{ fruitName }}</p>
      <p>Prediction Confidence: {{ predictionConfidence }}</p>
      <p>Nutritional Value: {{ nutritionalValue }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['fruitName', 'predictionConfidence'],
  data () {
    return {
      nutritionalValue: 'test'
    }
  }
}
</script>

<style lang="scss">
.output-section {
  text-align: center;
}
</style>
