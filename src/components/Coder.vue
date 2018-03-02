<template>
  <div class="modal" :class="showModal ? 'is-active' : ''">
    <div class="modal-background"></div>
    <div class="modal-card">
      <header class="modal-card-head">
        <p class="modal-card-title">{{ user }}</p>
        <button class="delete" aria-label="close" @click="showModal = false"></button>
      </header>
      <section class="modal-card-body">
        <img :src="val.avatar_url" />
        <p>{{ val.name }}</p>
        <p>ID: <strong>{{val.id }}</strong></p>
        <p>{{ val.bio }}</p>
        <p>Repos: <strong>{{ val.public_repos }}</strong></p>
        <p>Followers: <strong>{{ val.followers }}</strong></p>
        <p>Following: <strong>{{ val.following }}</strong></p>
        <p>Since: {{ val.created_at && val.created_at.substring(0, 10) }}</p>
        <p>{{ val.hireable && "Available for hire" }}</p>
        <p>{{ val.blog }}</p>
      </section>
      <footer class="modal-card-foot">
        <button class="button is-success">
          <a :href="'https://github.com/' + val.login" target="_blank">
            View Github repositories
          </a>
        </button>
        <button class="button is-success">
          <a :href="val.url" target="_blank">
            API data source
          </a>
        </button>
        <button class="button is-success" v-show="val.blog">
          <a :href="val.blog" target="_blank">
            Visit profile URL
          </a>
        </button>
        <button class="button" @click="showModal = false">Cancel</button>
      </footer>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
console.log(this.isVisible)
export default {
  props: ['user', 'showModal'],
  name: 'Coder',
  data () {
    return {
      val: ''
    }
  },
  async updated () {
    try {
      const response = await axios.get(`https://api.github.com/users/${this.user}`)
      this.val = response.data
    } catch (e) {
      console.log(e)
    }
  }

}
</script>

<style lang="scss" scoped>
   @import './coder.scss'
</style>
