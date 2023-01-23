<template>
  <router-view ></router-view>
  <Footer />
</template>


<script>
import Footer from './components/Footer'; 

export default {
  name: 'App',
  components:{
    Footer
  },
  methods: {

  },

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
