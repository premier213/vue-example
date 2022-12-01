<template>
  <div class="bg-blue-400 h-32">
    <h1 class="text-center text-white text-4xl pt-10">
      {{ title }}
    </h1>
  </div>
</template>

<script lang="ts">
export default {
  props: ["title"],
};
</script>
