<template>
    <div>
        <base-card>
            <base-button @resource-name="getResourceName" resourceName="stored-resources">Stored Resources</base-button>
            <base-button @resource-name="getResourceName" resourceName="add-resources">Add resources</base-button>
        </base-card>
        <component :is="resourcesName"></component>
    </div>
</template>

<script>
import StoredResources from "@/components/LearnResources/StoredResources";
import AddResources from "@/components/LearnResources/AddResources";

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
            resources: this.storedResources
        }
    },
    methods: {
        getResourceName(rs) {
            this.resourcesName = rs
        }
    },
    components: {
        StoredResources,
        AddResources
    }
}
</script>
