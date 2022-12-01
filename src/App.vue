<template>
  <div>
    <TheHeader title="Remember" />
    <div class="flex justify-center gap-4 py-4">
      <cmBtn
        title="Source"
        variant="info"
        @click="viewTab('CmSource')"
        :class="currentTab === 'CmSource' ? 'bg-pink-900' : 'bg-pink-600'"
      />
      <cmBtn
        title="Add Source"
        variant="info"
        @click="viewTab('AddSource')"
        :class="currentTab === 'AddSource' ? 'bg-pink-900' : 'bg-pink-600'"
      />
    </div>
    <KeepAlive> <Component :is="currentTab" /></KeepAlive>
  </div>
</template>

<script lang="ts">
import CmSource from "./components/learning-resources/CmSource.vue";
import TheHeader from "./components/layouts/TheHeader.vue";
import cmBtn from "./components/UI/BaseButton.vue";
import AddSource from "./components/learning-resources/AddSource.vue";
import type { AddData, Tab } from "./components/learning-resources/types";

export default {
  name: "App",
  components: {
    CmSource,
    AddSource,
    TheHeader,
    cmBtn,
  },
  data() {
    return {
      currentTab: "CmSource",
      selected: false,
      storedResources: [
        {
          id: "1",
          title: "vue.js",
          description: "official vue.js doc",
          link: "http://vuejs.org",
        },
        {
          id: "2",
          title: "react.js",
          description: "official react doc",
          link: "http://beta.react.org",
        },
      ],
    };
  },
  provide() {
    return {
      resource: this.storedResources,
      delete: this.remove,
      addData: this.add,
    };
  },
  methods: {
    viewTab(value: Tab) {
      this.currentTab = value;
    },
    remove(id: string) {
      const index = this.storedResources.findIndex((res) => res.id === id);
      this.storedResources.splice(index, 1);
    },
    add({ title, description, link }: AddData) {
      const value = {
        id: new Date().toISOString.toString(),
        title,
        description,
        link,
      };
      this.storedResources.unshift(value);
      this.currentTab = "CmSource";
    },
  },
};
</script>
