<script>
export default {
  name: "index",

  // async asyncData({$axios}) {
  //   const users = await $axios.$get("https://jsonplaceholder.typicode.com/users");
  //   return { users };
  // },  // work without store

  async fetch({store}) {
    if (store.getters["users/users"].length === 0) {
      await store.dispatch("users/fetch");
    }
  },

  data: () => ({
    pageTitle: "Users page"
  }),

  // async mounted() {
  //   await this.loadUsers();
  // },  // ClientSideRendering(CSR)

  computed: {
    users() {
      return this.$store.getters["users/users"];
    }
  },

  methods: {
    // async loadUsers() {
    //   const response = await this.$axios.get("https://jsonplaceholder.typicode.com/users");
    //   this.users = response.data;
    //   // console.log(this.users);
    // },
    openUser(user) {
      this.$router.push(`/users/${user.id}`);
    }
  }
}
</script>

<template>
  <section>
    <h1>{{ pageTitle }}</h1>
    <ul>
      <li v-for="user of users" :key="user.id">
        <a href="#" @click.prevent="openUser(user)">{{ user.name }}</a>
      </li>
    </ul>
  </section>
</template>

<style scoped></style>
