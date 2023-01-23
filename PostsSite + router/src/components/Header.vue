<template>
    <div>
        <h1> List of Users : </h1>
        <Buttons @btnClick="$emit('btnClick')" :text="nshow ? 'close' : 'new user'" :color="nshow ? 'red' : 'green' " />
    </div>
</template>

<script>
import Buttons from './Buttons';
export default {
    name:'home-name',
    components:{
        Buttons,
    },
    props:{
        nshow:Boolean
    }
}
</script>

<style scoped>
    div{
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;

    }
</style>