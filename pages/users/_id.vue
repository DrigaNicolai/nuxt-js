<script>
export default {
  name: "_id",

  validate({params}) {
    // console.log("Validate");
    return /^\d+$/.test(params.id);
  },

  async asyncData({$axios, params}) {
    const response = await $axios.get(`https://jsonplaceholder.typicode.com/users/${params.id}`);
    const user = response.data;
    return { user };
  }
}
</script>

<template>
  <section>
    <h1>{{ user.name }}</h1>
    <hr>
    <h3>{{ user.email }}</h3>
  </section>
</template>

<style scoped></style>
