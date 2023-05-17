<template>
    <img :src="url" :alt="titulo" />
</template>

<script>
export default{
    props: ['url', 'titulo']
}
</script>

<style>
.img-responsiva {
    width: 100%;
}
</style>