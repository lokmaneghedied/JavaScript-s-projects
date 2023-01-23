<template>
    <div>
        <h4 :style="{color:color}">Activity: ¨{{myActivity.activity}}¨ </h4>
        <p :style="{color:color}">Type: {{myActivity.type}} </p>
        <p :style="{color:color}">Participants: {{myActivity.participants}} persons </p>
        <p :style="{color:color}">Price: {{myActivity.price}} $ </p>

    </div>
</template>


<script>
export default {
    name:'quotesName',
    props:{
        myActivity:Object,
        color:String
    },
}
</script>

<style scoped>
    h4{
        display: flex;
        justify-content:  first baseline;
        align-items: center;
        text-align: center;
        padding: 10px;
    }
    p{
        display: flex;
        justify-content: first baseline;
        padding: 10px;
    }
    *{
        background: white;
        font-size:25px;
        font-family:'Times New Roman';  
        padding: 10px;
    }
    div{
        box-shadow: -0 -0 3px; 
    }
</style>