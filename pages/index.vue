<template>
  <section class="container">
    <div>
      <!-- {{ users[0].id }} -->
      <ul>
        <li v-for="user in users" :key="user.id">
          {{ user.id}}, {{user.name}},{{user.company.name}}
          error({ statusCode: e.response.status, message: e.message})
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
const axios = require('axios')
let url = 'https://jsonplaceholder.typicode.com/usersxxx'
export default {
  asyncData({ params }) {
    return axios.get(url) 
      .then((res) => {
        return { users: res.data }
      })
      .catch((e => {
        error({ users: e.response.status, message: 'Error!!!!!' })
      }))
  }
}
</script>
