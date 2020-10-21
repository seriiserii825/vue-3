<template>
  <div>
    <base-card>
      <base-button @click="getResourceName('stored-resources')">Stored Resources</base-button>
      <base-button @click="getResourceName('add-resources')">Add resources</base-button>
    </base-card>
    <keep-alive>
      <component :is="resourcesName"></component>
    </keep-alive>
  </div>
</template>

<script>
import StoredResources from "@/components/LearnResources/StoredResources";
import AddResources from "@/components/LearnResources/AddResources";
import BaseCard from "@/components/UI/BaseCard";
import BaseButton from "@/components/UI/BaseButton";

export default {
  data() {
    return {
      resourcesName: 'stored-resources',
      storedResources: [
        {
          id: '1',
          title: 'Vue',
          description: 'Vue js description',
          link: 'https://vuejs.org'
        },
        {
          id: '2',
          title: 'Google',
          description: 'Google js description',
          link: 'https://google.org'
        },
      ]
    }
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource
    }
  },
  methods: {
    getResourceName(rs) {
      this.resourcesName = rs
    },
    addResource(title, description, link) {
      const item = {id: Date.now, title, description, link}
      this.storedResources.unshift(item)
      this.resourcesName = 'stored-resource'
    }
  },
  components: {
    StoredResources,
    AddResources,
    BaseCard,
    BaseButton
  }
}
</script>
