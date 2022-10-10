<template>
    <header>
        <h1>{{ title }}</h1>
        <Button @toggle-add-task="$emit('toggle-add-task')" :text="showAddTask ? 'Close' : 'Add' " :color="showAddTask ? 'crimson' : 'green' "/>
    </header>
</template>

<script>
import Button from '@/components/Button'
export default {// component larni export import qiliw uchun 
  
    name: 'Header',// ismini registratsiya qlib olamiz 
    props:{ // props orqali component chaqiriw (yaniy ulaw!)
        title: String,
        showAddTask: Boolean,
    },
    components:{
        Button,
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