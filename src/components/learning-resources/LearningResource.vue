<template>
  <li
    class="flex flex-col items-center justify-center mt-4 w-1/2 m-auto border-b border-slate-300 py-4"
  >
    <div class="w-full">
      <header class="flex justify-between">
        <h3 class="text-xl">{{ title }}</h3>
        <cmBtn title="Delete" variant="error" @click="del(id)" />
      </header>
    </div>
    <p class="flex self-start my-4 text-slate-600">{{ description }}</p>
    <nav class="text-green-700 flex self-start">
      <a :href="link">View Link</a>
    </nav>
  </li>
</template>

<script lang="ts">
import cmBtn from "../UI/BaseButton.vue";
export default {
  props: ["title", "description", "link", "id"],
  inject: ["resource", "delete"],
  data: function () {
    return {
      del: this.delete,
    };
  },
  components: {
    cmBtn,
  },
};
</script>
