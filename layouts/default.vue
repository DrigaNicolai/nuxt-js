<script>
import Navbar from "~/components/Navbar";

export default {
  name: "default",

  components: { Navbar }
}
</script>

<template>
  <div class="default-layout">
    <Navbar />
    <main>
      <div class="container">
        <nuxt />
      </div>
    </main>
  </div>
</template>

<style>
.default-layout {
  margin: 10px;
}
.container {
  padding-top: 2rem;
  padding-left: 2rem;
  padding-right: 2rem;
}
</style>
