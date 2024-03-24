<template>
      <div>
        <h2>{{ Squirrel.unique_squirrel_id }}</h2>
        <h2>{{Squirrel.x}}, {{Squirrel.y}}</h2>
       
    </div>
</template>

<script setup>

const props = defineProps({
    Squirrel: Object,
}) 


</script>

<style lang="scss" scoped>

</style>