<template>
    <div class="container">
        <Header @btnClick="showAdd" :nshow= show />
      <div v-if=show >
        <NewUser @newUser = "addUser" />
      </div>
      <Users @deletedUser="deleteUser" @changedStatut="changeStatut" :key="users.length" :users="users" />
    </div>
</template>

<script>
import Header from '../components/Header'; 
import Users from '../components/Users';
import NewUser from '../components/NewUser';

export default {
  name: 'HomeView',
  data(){
    return {
      show : false,
      users:[],
    }
  },
  components:{
    Header,
    Users,
    NewUser,
  },
  methods:{
    showAdd(){
      this.show = !this.show
    },
    async deleteUser(id){
      const res = await fetch(`http://localhost:5000/users/${id}`,{
        method : 'DELETE',
      })
      res.status === 200 ? this.users = this.users.filter((user)=> user.id !== id) : alert("error deleting user")
    },
    async changeStatut(id){
      const userToChange = await this.fetchUser(id)
      const changedUser = {...userToChange, statut:!userToChange.statut}
      const res = await fetch(`http://localhost:5000/users/${id}`,{
        method:'PUT',
        headers : {'Content-type':'application/json'} ,
        body : JSON.stringify(changedUser)
      })
        const data = await  res.json()
        this.users = this.users.map((user)=> user.id == id ? {...user , statut:data.statut} : user)
    },
    async addUser(x){
      const res = await fetch('http://localhost:5000/users',{
        method : 'POST',
        headers : {'Content-type':'application/json'} ,
        body: JSON.stringify(x)
      })
      const data = await res.json()
      this.users = [...this.users , data]
    },
    async fetchUsers(){
      const res = await fetch('http://localhost:5000/users')
      const data = await res.json()
      return data
    },
    async fetchUser(id){
      const res = await fetch(`http://localhost:5000/users/${id}`)
      const data = await res.json()
      return data
    }
  },
  async created() {
    this.users = await this.fetchUsers()
  },
}
</script>
