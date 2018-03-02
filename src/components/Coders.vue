<template>
  <div class="coders">

    <div v-for="row in Math.floor(users.length/col)">
      <div class="tile is-ancestor">
        <div class="tile is-parent" v-for="(user, key) of users.slice(col*(row-1), col*row)">
          <article class="tile is-child box" :href="user.html_url">
            <p class="title" @click="showDetails(key+col*(row-1))">
              <img :src="user.avatar_url" />
            </p>
            <p class="subtitle">{{user.login}}</p>
          </article>
        </div>
      </div>
    </div>

    <Coder v-show="selectedUser" v-bind:user="selectedUser"  v-bind:showModal="true"/>

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
      col: Math.floor(window.screen.width / 225),
      users: [],
      selectedUser: null
    }
  },
  methods: {
    showDetails (id) {
      console.log(this.users[id].login)
      this.selectedUser = this.users[id].login
    }
  },
  async created () {
    try {
      const response = await axios.get(`https://api.github.com/search/users?q=location:Wroclaw+location:Wrocław?&per_page=21`)
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
  cursor: pointer;
}
p {
  color: #008000;
}
</style>
