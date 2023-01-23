<template>  
    <footer><a href="http://google.com" target="_blank" >by {{text}}</a></footer>      
</template>

<script>
export default {
    name:'footerName',
    props:{
        text: String
    }
}
</script>


<style scoped>
    footer{
        display: flex;
        justify-content: center;
        color: white;
        font-size:15px;
        font-family:'Times New Roman';  
        padding: 10px;

    }
    a{
        color:white
    }
</style>