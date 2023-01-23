<template>
  <div class="container">
    <Header @btnClick="showAdd" :nshow= show />
    <div v-if=show >
      <NewPost @newPost = "addPost" />
    </div>
    <div v-if="showSave">
      <ChangedPost @newChangedPost="changedPost" />
    </div>
    <Posts @myPost="getPost" @deletedPost="deletePost" :key="posts.length" :posts="posts" />
  </div>
  <Footer />
</template>


<script>
import Header from './components/Header'; 
import Footer from './components/Footer'; 
import Posts from './components/Posts';
import NewPost from './components/NewPost';
import ChangedPost from './components/ChangedPost';

export default {
  name: 'App',
  data(){
    return {
      showSave:false,
      show: false,
      myPost : '',
      posts:[],
    }
  },
  components:{
    Header,
    Footer,
    Posts,
    NewPost,
    ChangedPost
  },
  methods: {
    async deletePost(id) {
      await fetch(`http://127.0.0.1:5000/posts/delete/${id}`,{
        method: 'DELETE',
        headers: { 'Content-type': 'application/json' },
      })
      this.posts = await this.fetchPosts()
    },
    async getPost(post) {
      this.showSave = true
      this.myPost = post
    },
    async changedPost(post) {
      this.myPost.title = post.title
      this.myPost.content = post.content
      this.myPost.author = post.author
      await fetch(`http://127.0.0.1:5000/posts/edit`,{
         method: 'PUT',
         headers: { 'Content-type': 'application/json' },
         body: JSON.stringify(this.myPost)
      })
      this.showSave = false
    },
    async addPost(x){
      await fetch('http://127.0.0.1:5000/posts/new_post',{
        method : 'POST',
        headers : {'Content-type':'application/json'} ,
        body: JSON.stringify(x)
      })
      this.posts = await this.fetchPosts()
    },
    showAdd(){
      this.show = !this.show
    },
    async fetchPosts(){
      const res = await fetch('http://127.0.0.1:5000/posts')
      const data = await res.json()
      return data['posts']
    },
  },
  async created() {
    this.posts = await this.fetchPosts()
  }
}
</script>


<style>
  .container{
    max-width: 500px;
    margin: 30px auto;
    overflow: auto;
    min-height: 300px;
    border:1px solid steelblue;
    padding: 30px;
    border-radius: 5px;
  }
</style>
