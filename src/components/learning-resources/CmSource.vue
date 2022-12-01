<template>
  <ui class="flex flex-col">
    <LearningResource
      v-for="res in iterable"
      :key="res.id"
      :title="res.title"
      :description="res.description"
      :link="res.link"
      :id="res.id"
    />
  </ui>
</template>

<script lang="ts">
import LearningResource from "./LearningResource.vue";
export default {
  inject: ["resource", "delete"],
  components: {
    LearningResource,
  },
  data() {
    return {
      iterable: this.resource,
      del: this.delete,
    };
  },
  provide() {
    return {
      del: (id: string) => this.del(id),
    };
  },
};
</script>
