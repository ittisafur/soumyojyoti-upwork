<template>
  <div class="max-w-2xl mx-auto my-20">
    <h2 class="text-3xl uppercase text-center text-gray-300 font-extrabold">
      Vue todo
    </h2>

    <api endpoint="todos?_sort=id&_order=desc">
      <div
        class="flex flex-col space-y-2 mt-4"
        slot-scope="{ data: todos, remove, create: createOnServer }"
      >
        <composer @submitted="(task) => addTodo(task, createOnServer)" />
        <Todo
          v-for="todo in todos"
          :key="todo.id"
          :todo="todo"
          @delete="remove"
        />
      </div>
    </api>
  </div>
</template>

<script>
export default {
  head: {
    bodyAttrs: {
      class: "bg-gray-800",
    },
  },
  methods: {
    async addTodo(task, createOnServer) {
      const todo = {
        task,
        done: false,
        id: Date.now(),
      };
      await createOnServer(todo);
    },
  },
};
</script>
