<template>
    <footer>
        <p>welcom to users</p>
        <router-link to="/about">  About </router-link>
    </footer>
</template>

<script>
export default {
name:'FooterName'
}
</script>

<style scoped>
footer {
display: block;
margin: 30px auto;
min-height: 10px;
border:1px solid steelblue;
padding: 30px;
border-radius: 5px;
}
</style>