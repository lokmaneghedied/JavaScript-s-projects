<template>
    <div :key="user.id" v-for="user in users">
        <User @deletedUser="$emit('deletedUser',user.id)" @changedStatut="$emit('changedStatut', user.id)" :user="user" />
    </div>
</template>

<script>
import User from './User'
export default {
    name:'users-name',
    props:{
        users:Array,
    },
    components:{
        User,
    },
    emits:["deletedUser","changedStatut"]
}
</script>