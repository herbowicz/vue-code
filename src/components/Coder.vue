<template>
  <div>
    <a :href="val.login" target="_blank">
      <h2>{{ user }}</h2>
    </a>
    <ul>
      <li>{{ val.name }}</li>
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
  </div>
</template>

<script>
import axios from 'axios'

export default {
  props: ['user'],
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
</style>

