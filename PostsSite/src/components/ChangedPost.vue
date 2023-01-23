<template>
    <form @submit.prevent="save">
        <div>
            <input type="text" placeholder="title" v-model="title" required>
            <input type="text" placeholder="content" v-model="content" required>
            <input type="text" placeholder="author" v-model="author" required>
        </div>
            <button type="submit" class="btn">Save</button>
    </form>

</template>


<script>
export default {
    name: 'ChangedPost',
    data() {
        return {
            title: '',
            content: '',
            author:''
        }
    },
    props: {
        myChangedPost:Object
    },
    methods: {
        save() {
            const newChangedPost = {
                title: this.title,
                content: this.content,
                author: this.author
            };
            this.title =  '' ;
            this.content =  '' ;
            this.author = '';
            this.$emit('newChangedPost', newChangedPost)
        }
    }
}
</script>


<style>
form {
    display: grid;
    justify-content: left;
    background: rgb(211, 214, 245);
    padding: 10px 20px;
    border-radius: 10px;
    margin: 5px;
    font-size: 15px;
    font-family: inherit;

}

.btn {
    display: inline-block;
    background: green;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 10px;
    cursor: pointer;
    font-size: 15px;
    font-family: inherit;
}
</style>