<template>
  <div class="flex flex-col justify-center mt-4 w-1/3 m-auto py-4">
    <form @submit.prevent="submitData">
      <div class="flex flex-col">
        <label for="title">Title:</label>
        <input
          type="text"
          name="title"
          id="title"
          class="border-slate-400 border rounded-md w-1/2 h-12"
          ref="title"
        />
      </div>
      <div class="flex flex-col">
        <label for="link">link:</label>
        <input
          type="url"
          name="link"
          id="link"
          class="border-slate-400 border rounded-md w-1/2 h-12"
          ref="link"
        />
      </div>
      <div class="flex flex-col">
        <label for="description">Description:</label>
        <textarea
          name="description"
          id="description"
          cols="10"
          rows="5"
          class="border-slate-400 border rounded-md w-1/2"
          ref="desc"
        ></textarea>
      </div>
      <div class="flex flex-col py-4">
        <cmBtn title="Submit" variant="link" type="submit" />
      </div>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import cmBtn from "../UI/BaseButton.vue";

export default defineComponent({
  components: {
    cmBtn,
  },
  inject: ["addData"],
  methods: {
    submitData() {
      const title = (this.$refs.title as HTMLInputElement).value;
      const link = (this.$refs.link as HTMLInputElement).value;
      const description = (this.$refs.desc as HTMLTextAreaElement).value;
      this.addData({ title, link, description });
      this.$refs.link.value = null;
      this.$refs.desc.value = null;
      this.$refs.title.value = null;
    },
  },
});
</script>
