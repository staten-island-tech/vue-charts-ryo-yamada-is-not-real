<template>
      <div>
        <h2>{{ Squirrel.unique_squirrel_id }}</h2>
        <h2>{{Squirrel.x}}, {{Squirrel.y}}</h2>
       
    </div>
</template>

<script setup>
import { GoogleMap, Marker } from 'vue3-google-map'

const props = defineProps({
    Squirrel: Object,
}) 


</script>

<style lang="scss" scoped>

</style>