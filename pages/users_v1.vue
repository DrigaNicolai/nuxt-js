<script>
export default {
  name: "users",

  async asyncData() {
    console.log("Async Data");
    const response = await fetch("https://jsonplaceholder.typicode.com/users?_limit=5");
    await new Promise(resolve => setTimeout(() => resolve(), 1200)) // To test loading
    const users = await response.json();
    return { users_v1 };
  },

  data: () => ({
    users: []
  }),

  async mounted() {
    // await this.getUsers();
  },

  methods: {
    async getUsers() {
      const response = await fetch("https://jsonplaceholder.typicode.com/users?_limit=5");
      this.users = await response.json();
      // console.log(users);
    }
  }
}
</script>

<template>
  <div>
    <h1>Users page</h1>
    <hr>
    <ul>
      <li v-for="user in users" :key="user.id">
        {{ user.name }}
      </li>
    </ul>
    <hr>
    <button @click="$router.push('/')">Home</button>
  </div>
</template>

<style scoped>
hr {
  margin-top: 2rem;
  margin-bottom: 2rem;
}
</style>
