<template>
  <div class="container column">
    <app-form @loadInformation="loadInformation"></app-form>
    <app-view :properties="properties"></app-view>
  </div>

  <div class="container">
    <app-comments :comments="comments" @loadComments="loadComments"></app-comments>
    <app-loader v-if="loader"></app-loader>
  </div>
</template>

<script>
import axios from 'axios'
import AppForm from './components/AppForm.vue'
import AppView from './components/AppView.vue'
import AppComments from './components/AppComments.vue'
import AppLoader from './components/AppLoader.vue'

export default {
  data() {
    return {
      properties: [],
      comments: [],
      loader: false
    }
  },
  emits: ['loadInformationToView'],
  methods: {
    loadInformation(data) {
      this.properties.push(data)
    },
    async loadComments() {
      this.loader = true
      const { data } = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = data
      this.loader = false
    }
  },
  components: { AppForm, AppView, AppComments, AppLoader }
}
</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
