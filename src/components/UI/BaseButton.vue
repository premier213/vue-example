<template>
  <button :class="varia" class="text-sm border px-4 rounded">
    {{ title }}
  </button>
</template>

<script lang="ts">
import { defineComponent, type PropType } from "vue";
import type Button from "./button";

export default defineComponent({
  name: "cmBtn",
  props: {
    title: {
      type: String as PropType<Button["title"]>,
    },
    variant: {
      type: String as PropType<Button["variant"]>,
    },
    class: {
      type: String,
    },
  },
  computed: {
    varia() {
      switch (this.variant) {
        case "error":
          return "border-red-500 text-red-500";
        case "link":
          return "text-white bg-blue-500 rounded-md w-32 py-4";
        case "info":
          return `${this.class} p-4 text-xl text-slate-200`;
        default:
          break;
      }

      return "";
    },
  },
});
</script>
