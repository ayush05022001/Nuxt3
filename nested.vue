<template>
    <div>

    </div>
</template>

<script setup>
const paragraphs = ref()

const route = useRoute()

const { data: page } = await useFetch(`/api/page/${route.params.slug}`)


watch(page, (newPage)=>{
    if (newPage.Id) {

      useFetch(`/api/page/${newPage.Id}/paragraphs`).then((response)=>{
         paragraphs.value  = response.data

     })
        
    }
}, {
    deep: true,
    immediate:true
})
</script>

<style lang="scss" scoped>

</style>