<template>
    <ul>
        <learn-resource
            v-for="res in resources"
            :key="res.id"
            :id="res.id"
            :title="res.title"
            :description="res.description"
            :link="res.link"
        ></learn-resource>
    </ul>
</template>

<script>
import LearnResource from "@/components/LearnResources/LearnResource";

export default {
    inject: ['resources'],
    components: {
        LearnResource
    }
}
</script>

<style scoped lang="scss">
ul {
  list-style: none;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
