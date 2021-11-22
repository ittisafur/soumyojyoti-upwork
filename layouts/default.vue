<template>
  <div>
    <main>
      <Nuxt />
    </main>
    <footer>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: "mdi-apps",
          title: "Welcome",
          to: "/",
        },
      ],
    };
  },
};
</script>
