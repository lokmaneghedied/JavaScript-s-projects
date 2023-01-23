<template>
    <div :key="post.id" v-for="post in posts">
        <Post @deletedPost="$emit('deletedPost',post.id)" :post="post"  @myPost="$emit('myPost',post)"/>
    </div>
</template>

<script>
import Post from './Post'
export default {
    name: 'PostsName',
    props:{
        posts:Array,
    },
    components:{
        Post,
    },
    emits: ["deletedPost","myPost"]
}
</script>

