<template>
  <div>
    <div class="upload-section has-text-white">
      <h1 class="title-margin has-text-white">Upload Fruit Image</h1>
      <b-field>
        <b-upload v-model="dropFile" drag-drop accept="image/*">
          <section class="section">
            <div class="content has-text-centered">
              <p>
                <b-icon icon="upload" size="is-large"></b-icon>
              </p>
              <p>Drop your files here or click to upload</p>
            </div>
          </section>
        </b-upload>
      </b-field>
      <div>
        <span v-if="dropFile">
          {{dropFile.name}}
        </span>
        <b-button type="is-danger" size="is-small" @click="deleteDropFile()">Delete</b-button>
      </div>
    </div>
    <div class="predict-btn-section">
      <b-button @click="onClick" type="is-light" rounded expanded>Get Fruit Nutrition</b-button>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      dropFile: null
    }
  },
  mounted () {
    axios.get('https://dl-image-classification-api.herokuapp.com/')
      .then((response) => {
        console.log('Started Application.')
      })
  },
  methods: {
    deleteDropFile () {
      this.dropFile = null
    },
    onClick () {
      if (this.dropFile) {
        const config = {
          headers: {
            'Content-Type': 'multipart/form-data'
          }
        }
        let formData = new FormData()
        let uploadFile = this.dropFile
        formData.append('photo', uploadFile)
        axios.post('https://dl-image-classification-api.herokuapp.com/model', formData, config)
          .then((response) => {
            console.log(response.data)
            this.fruitName = response.data.fruitName
            this.$emit('prediction', {
              'fruitName': this.fruitName
            })
          })
      } else {
        this.$buefy.notification.open({
          message: 'Please upload the image of a fruit.',
          type: 'is-danger'
        })
      }
    }
  }
}
</script>

<style lang="scss">
.upload-section {
  text-align: center;
}
.title-margin {
  margin-top: 3rem;
  margin-bottom: 6rem;
}
.margin-1 {
  margin: 1rem;
}
.predict-btn-section {
  margin: 6rem 4rem;
}
</style>
