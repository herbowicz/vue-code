<template>
  <div class="coders">
    <ul v-if="users && users.length">
      <li v-for="(user, key) of users">
        <a :href="user.html_url">
          <img @mouseover="showDetails(key)" @mouseout="hideDetails()" :src="user.avatar_url" />
        </a>
      </li>
    </ul>
    <Coder v-show="selectedUser" v-bind:user="selectedUser" /> 
  </div>
</template>

<script>
import axios from 'axios'
import Coder from './Coder'

export default {
  name: 'Coders',
  components: {
    Coder
  },
  data () {
    return {
      users: [],
      selectedUser: null
    }
  },
  methods: {
    showDetails (id) {
      this.selectedUser = this.users[id].login
      console.log(1)
    },
    hideDetails () {
      this.selectedUser = null
    }
  },
  async created () {
    try {
      const response = await axios.get(`https://api.github.com/search/users?q=location:Wroclaw+location:Wrocław?&per_page=14`)
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
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0;
}

a {
  color: #35495E;
}

img {
  width: 100px;
  height: 100px;
}
</style>
