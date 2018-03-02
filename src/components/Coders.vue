<template>
  <div class="coders">

    <div v-for="i in Math.floor(users.length/cols)">
      <div class="tile is-ancestor">
        <div class="tile is-parent" v-for="(user, key) of users.slice(cols*(i-1), cols*i)">
          <article class="tile is-child box" :href="user.html_url">
            <p class="title"><img @mouseover="showDetails(key)" @mouseout="hideDetails()" :src="user.avatar_url" /></p>
            <p class="subtitle">{{user.login}}</p>
          </article>
        </div>
      </div>
    </div>

    <Coder v-show="selectedUser" v-bind:user="selectedUser" />
  </div>
</template>

<script>
import 'bulma/css/bulma.css'
import axios from 'axios'
import Coder from './Coder'

export default {
  name: 'Coders',
  components: {
    Coder
  },
  data () {
    return {
      cols: Math.floor(window.screen.width / 225),
      users: [],
      selectedUser: null
    }
  },
  methods: {
    showDetails (id) {
      this.selectedUser = this.users[id].login
    },
    hideDetails () {
      this.selectedUser = null
    }
  },
  async created () {
    try {
      const response = await axios.get(`https://api.github.com/search/users?q=location:Wroclaw+location:Wrocław?&per_page=25`)
      this.users = response.data.items
    } catch (e) {
      console.log(e)
    }
  }

  // using a Promise
  // created () {
  //   axios.get(`https://api.github.com/search/users?q=location:Wroclaw+location:Wrocław?&per_page=3`)
  //     .then(response => {
  //     // JSON responses are automatically parsed.
  //       this.users = response.data.items
  //     })
  //     .catch(e => {
  //       this.errors.push(e)
  //     })

}
</script>

<style scoped>
img {
  border: 2px solid #008000;
  padding: 5px;
  border-radius: 50%;
}
p {
  color: #008000;
}
</style>
