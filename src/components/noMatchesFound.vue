<template>

    <div class="container">
        <h1 class="title-style pt-5">{{message}}</h1>
    </div>

</template>

<script>

export default {
    name: 'noMatchesFound',
    props: {
        message:String,
    }
}
</script>

<style scoped>

    .container {
        text-align: center;
    }

    .title-style{
        font-size: 25px;
        color: #656565;
        margin: 0;
    }

    .img-style{
        width: 20rem;
        height: 20rem;
    }

</style>
