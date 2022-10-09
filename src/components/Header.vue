<template>
    <header>
        <h1>{{ title }}</h1>
    </header>
</template>

<script>
export default {// component larni export import qiliw uchun 
    name: 'Header',// ismini registratsiya qlib olamiz 
    props:{ // props orqali component chaqiriw (yaniy ulaw!)
        title: String,
    }
}
</script>

<style>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>