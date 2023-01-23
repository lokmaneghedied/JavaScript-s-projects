<template>
    <button @click="btnClick" :style="{background:color}">{{text}}</button>
</template>

<script>
export default {
    name:'button-name',
    props:{
        text : String,
        color : String
    },
    methods:{
        btnClick(){
            this.$emit("btnClick");
        }
    }
}
</script>


<style scoped>
  button{
        display:inline-block;
        background: #000;
        color: #fff;
        border:none;
        padding: 10px 20px;
        margin: 5px;
        border-radius:5px;
        cursor: pointer;
        text-decoration:none;
        font-size:15px;
        font-family:inherit;    }
</style>
