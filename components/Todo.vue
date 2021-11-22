<template>
  <div class="flex justify-between items-center bg-gray-900 p-4 text-white">
    <p>{{ todo.task }}</p>
    <div>
      <button
        @click="$emit('delete', todo.id)"
        class="text-red-500 font-bold text-2xl"
      >
        &times;
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["todo"],
};
</script>