<template>
    <div>
        <h1>My Project: ID</h1>
        <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Deserunt, natus. Hic molestiae illo consectetur itaque dicta officiis amet sapiente similique, cupiditate minus necessitatibus, corporis numquam! Est, minima! Ad, saepe incidunt!</p>
        <ContentRenderer v-if="data" :value="data" />
    </div>
</template>

<script setup>
const { path } = useRoute()

const { data } = await useAsyncData(`content-${path}`, () => {
  return queryContent().where({ _path: path }).findOne()
})
</script>