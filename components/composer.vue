<template>
  <form @submit.prevent="handleSubmit" class="mt-4">
    <input
      type="text"
      v-model="newTask"
      class="w-full bg-gray-900 p-4 focus:outline-none text-gray-300"
      placeholder="Type and hit enter"
    />
  </form>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
    };
  },
  methods: {
    handleSubmit() {
      this.$emit("submitted", this.newTask);
      this.newTask = "";
    },
  },
};
</script>