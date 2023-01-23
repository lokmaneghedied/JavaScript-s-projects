<template>
    <div :class="[user.statut ? 'statut' : '', 'user']" @dblclick="$emit('changedStatut', user.id)">
        <h3 >{{user.name}} 
            <i @click="$emit('deletedUser', user.id)" class="fas fa-times"></i> 
        </h3>
        <p>{{user.mail}}</p>
    </div>
</template>

<script>
    export default{
        name: 'user-name',
        props:{
            user:Object,
        }
    }
</script>

<style>
    .user{
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
    }
    .user.statut{
        border-left: 5px solid green;
    }
</style>