<template>

    <div class="modal" :class="showModal ? 'is-active' : ''">
      <div class="modal-background"></div>
      <div class="modal-card">
        <header class="modal-card-head">
          <p class="modal-card-title">{{ user }}</p>
          <button class="delete" aria-label="close" @click="showModal = false"></button>
        </header>
        <section class="modal-card-body">
          <a :href="val.login" target="_blank">
            <h2>{{ val.name }}</h2>
          </a>
          <ul>
            <li>ID: {{val.id }}</li>
            <li>{{ val.bio && val.bio.substring(0, 80) }}</li>
            <li>Repos: <strong>{{ val.public_repos }}</strong></li>
            <li>Followers: {{ val.followers }}</li>
            <li>Following: {{ val.following }}</li>
            <li>Since: {{ val.created_at && val.created_at.substring(0, 10) }}</li>
            <li>{{ val.hireable && "Available for hire" }}</li>
            <li>
              <a :href="val.blog" target="_blank">
                {{ val.blog && val.blog.substr(val.blog.indexOf('://') + 3) }}
              </a>
            </li>
          </ul>
        </section>
        <footer class="modal-card-foot">
          <button class="button is-success">Save changes</button>
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

<style>
ul {
  list-style-type: none;
}
.moreInfo {
  position: absolute;
  top: 0;
  z-indes: 5;
}
</style>
