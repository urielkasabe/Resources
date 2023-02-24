<template>
  <base-card>
    <base-button @click="SwitchTab('stored-res')" :mode="checkSelectedTabStored"
      >Stored Resources</base-button
    >
    <base-button @click="SwitchTab('add-res')" :mode="checkSelectedTabAdd"
      >Add Resource</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import storedRes from './storedRes.vue';
import AddRes from './AddRes.vue';

export default {
  components: { storedRes, AddRes },
  data() {
    return {
      selectedTab: 'stored-res',
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js doccumatation',
          link: 'http://vuejs.org',
        },
        {
          id: 'github',
          title: 'GitHub',
          description: 'cloud repository in which you can save your code',
          link: 'https://github.com/',
        },
      ],
    };
  },
  provide() {
    return {
      Res: this.storedResources,
      addResource: this.AddResource,
      deleteRes: this.removeResource
    };
  },
  methods: {
    SwitchTab(tab) {
      this.selectedTab = tab;
    },
    AddResource(title, desc, url) {
      const newRes = {
        id: new Date().toISOString(),
        title: title,
        description: desc,
        link: url,
      };
      this.storedResources.unshift(newRes);
      this.selectedTab = 'stored-res';
    },
    removeResource(resId) {
        const resIndex = this.storedResources.findIndex(res => res.id === resId);
        this.storedResources.splice(resIndex, 1);
    }
  },
  computed: {
    checkSelectedTabStored() {
      return this.selectedTab === 'stored-res' ? null : 'flat';
    },
    checkSelectedTabAdd() {
      return this.selectedTab === 'add-res' ? null : 'flat';
    },
  },
};
</script>