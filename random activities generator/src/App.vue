<template>  
<div class="myclass" :style="{background:ncolor}">
    <div class="homePage">
      <div class="container">
        <Activity :myActivity="myActivity" :color="this.ncolor" />
        <Buttons @btnClick="btnClick" :color="this.ncolor" />
      </div>
      <Footer text="lokmane" />
    </div>
</div>
</template>


<script>
import Activity from './components/Activity'
import Buttons from './components/Buttons'
import Footer from './components/Footer'

export default {
  name:'App',
  data(){
    return{
      ncolor:'',
      colors:['rgb(32, 30, 30)','rgb(124, 106, 106)','rgb(247, 219, 219)','rgb(233, 125, 125)','rgb(228, 210, 50)','rgb(150, 135, 1)','rgb(60, 241, 4)','rgb(2, 183, 255)','rgb(17, 0, 250)','rgb(255, 0, 255)','rgb(255, 0, 0)'],
      myActivity:{
        activity:"",
        type:"",
        participants:"",
        price:"",

      }
    }
  },
  components:{
    Buttons,
    Activity,
    Footer
  },
    methods: {
      async btnClick(){
        this.ncolor=this.colors[Math.floor(Math.random() * this.colors.length)]
        this.myActivity =await this.fetchActivity()
      },
      async fetchActivity(){
        const res = await fetch('http://127.0.0.1:5000/posts')
        const data = res.json()
        return data
      }
  },
  async created(){
    this.myActivity = await this.fetchActivity()
  }
}
</script>


<style>
  .container{
    border:none ;
    padding: 30px;
    max-width: 600px;
    border-radius: 5px;
    background: white;
    box-shadow: 0 0 10px;
  }
  .myclass{
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
  }
  *{
    margin: 0px;
  }
</style>