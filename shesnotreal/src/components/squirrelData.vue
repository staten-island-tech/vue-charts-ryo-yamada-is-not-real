<template>
    <div>
        <h2>{{ Squirrel.unique_squirrel_id }}</h2>
        <h2>{{Squirrel.x}}, {{Squirrel.y}}</h2>
    </div>
</template>

<script setup>
const props = defineProps({
    Squirrel: Object,
}) //if i change it from Squirrel to something else the code get very angry


</script>

<style lang="scss" scoped>

</style>