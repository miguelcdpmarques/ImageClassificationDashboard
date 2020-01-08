<template>
  <div class="columns full-page">
    <div class="column input-section">
      <inputs @prediction="updatePrediction"></inputs>
    </div>
    <div class="column output-section">
      <outputs :fruitName="fruitName"></outputs>
    </div>
  </div>
</template>

<script>
import Inputs from '@/components/Inputs.vue'
import Outputs from '@/components/Outputs.vue'

export default {
  name: 'home',
  components: {
    Inputs,
    Outputs
  },
  data () {
    return {
      fruitName: ''
    }
  },
  methods: {
    updatePrediction (value) {
      this.fruitName = value.fruitName
      console.log('New class: ', this.fruitName)
    }
  }
}
</script>

<style lang="scss">
.full-page {
  height: 100vh;
}
.input-section {
  background-color: #44546aff;
  border: 1px solid black;
}
</style>
