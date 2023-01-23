<template>
    <form @submit.prevent="add" >
    <div class="first">
        <input type="text" placeholder="name" v-model="name" required>
        <input type="text" placeholder="email" v-model="mail" required>
    </div>
    <div class="second">
        <input type="checkbox" v-model="statut" >
        <label for="checkbox">On-ligne</label>
    </div>
        <button type="submit" class="btn">create</button>
    </form>
</template>


<script>
export default {
    name:'NewUser',
    data(){
        return{
            name:'',
            mail:'',
            statut:false
        }
    },
    methods:{
        add(){
            let newUser = {
                id: ((Math.random())*10000).toFixed(0),
                name: this.name,
                mail: this.mail,
                statut: this.statut,
            };
            this.name = '' ;
            this.mail = '' ;
            this.statut = '' ;

            this.$emit('newUser',newUser);
        }
    }
}
</script>

<style>
    form{
        background: rgb(211, 214, 245);
        padding: 10px 20px;
        border-radius:10px;
        margin: 5px;
        font-size:15px;
        font-family:inherit;  
  
    }
    .btn{
        display:inline-block;
        background: green;
        color: #fff;
        border:none;
        padding: 10px 20px;
        margin: 5px;
        border-radius:10px;
        cursor: pointer;
        font-size:15px;
        font-family:inherit;    
    }
</style>