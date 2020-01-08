<template>
  <div class="output-section">
    <h1 class="title-margin">Nutrition Analysis</h1>
    <div class="results-section is-centered">
      <p>Fruit Name: {{ fruitName }}</p>
      <div class="table-container">
        <table class="table text-center is-bordered is-narrow is-striped margin-auto" v-if="fruitName">
          <thead>
            <tr>
              <th>Nutrition</th>
              <th class="value-width">Value</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>Energy (kcal)</td>
              <td class="text-align-right">{{ nutritionalValue[0]['energy (Kcal)'] }}</td>
            </tr>
            <tr>
              <td>Water (%)</td>
              <td class="text-align-right">{{ nutritionalValue[0]['water (%)'] }}</td>
            </tr>
            <tr>
              <td>Fiber (g)</td>
              <td class="text-align-right">{{ nutritionalValue[0]['fiber (g)'] }}</td>
            </tr>
            <tr>
              <td>Fat (g)</td>
              <td class="text-align-right">{{ nutritionalValue[0]['fat (g)'] }}</td>
            </tr>
            <tr>
              <td>Protein (g)</td>
              <td class="text-align-right">{{ nutritionalValue[0]['protein (g)'] }}</td>
            </tr>
            <tr>
              <td>Sugar (g)</td>
              <td class="text-align-right">{{ nutritionalValue[0]['sugar (g)'] }}</td>
            </tr>
            <tr>
              <td>Vit. A (ug)</td>
              <td class="text-align-right">{{ nutritionalValue[0]['vit.A (ug)'] }}</td>
            </tr>
            <tr>
              <td>Vit. B1 (mg)</td>
              <td class="text-align-right">{{ nutritionalValue[0]['vit.B1 (mg)'] }}</td>
            </tr>
            <tr>
              <td>Vit. B2 (mg)</td>
              <td class="text-align-right">{{ nutritionalValue[0]['vit.B2 (mg)'] }}</td>
            </tr>
            <tr>
              <td>Vit. B6 (mg)</td>
              <td class="text-align-right">{{ nutritionalValue[0]['vit.B6 (mg)'] }}</td>
            </tr>
            <tr>
              <td>Vit. C (mg)</td>
              <td class="text-align-right">{{ nutritionalValue[0]['vit.C (mg)'] }}</td>
            </tr>
            <tr>
              <td>Vit. E (mg)</td>
              <td class="text-align-right">{{ nutritionalValue[0]['vit.E (mg)'] }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import fruitData from '@/assets/fruits.json'

export default {
  props: ['fruitName'],
  data () {
    return {
      columns: [
        {
          field: 'first_name',
          label: 'Nutrient'
        },
        {
          field: 'second_name',
          label: 'Value'
        }
      ]
    }
  },
  computed: {
    nutritionalValue () {
      return fruitData['fruits'].filter((fruit) => fruit.name === this.fruitName)
    }
  }
}
</script>

<style lang="scss">
.output-section {
  text-align: center;
}
.value-width {
  width: 5rem;
}
.margin-auto {
  margin: auto;
}
td.text-align-right {
  text-align: right !important;
}
</style>
