<template>
    <div>
        <h3 @dblclick="$emit('myPost',post)">{{post.title}} 
            <i @click="$emit('deletedPost', post.id)" class="fas fa-times"></i> 
        </h3>
        <p>content: {{post.content}}</p>
        <p>author: {{post.author}}</p>
    </div>
</template>

<script>
    export default{
        name: 'PostName',
        props:{
            post:Object,
        }
    }
</script>

<style>
.post{
        background: #f4f4f4;
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
        border-radius:10px;

    }
    .fas{
        color:red
    }
    h3 {
        display: flex;
        align-items: center;
        justify-content: space-between;
        background: #0509f7;
        margin: 5px;
        padding: 10px 20px;
    }
    p{
        background: #f4f4f4;
        margin: 5px;
        padding: 10px 20px;
    }
    /* .post.statut{
        border-left: 5px solid green;
    } */
</style>