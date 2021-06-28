<template>
  <div class="index_page" >
    <h1 class="titre">User list</h1>
    <button @click="showCard(isDisplay = !isDisplay)"  class="btnS">{{this.btnAction}}</button>
    <div class="box4" v-if="isDisplay == true" >
      <Card :username="p.username" :company="'phone' + p.company.name" :adresse="p.address.city" :phone="p.phone" v-for="p in users" :key="p.id"/>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Card from "../components/Card.vue";

export default {
    data() {
    return {
      btnAction : "",
      isDisplay : false,
      filterUsers: [],
      users: [],
    }
  },
    mounted(){
      this.getUsers()

    },
    methods: {
      getUsers(){
        axios.get("https://jsonplaceholder.typicode.com/users").then(response=>{
        this.users = response.data;
        /*this.filterUsers = response.data;*/
        console.log(this.users)
        })
      },
      showCard(){
        this.btnAction = "Show Card"
      }
    },
    component:{
      Card
    }

}
</script>
<style lang="scss">
.index_page{
  width: 100%;
  display: flex;
  flex-direction: column;
  .titre{
  font-weight: 600;
  color: yellow;
  font-size: 65px;
  margin: auto;
  text-transform: uppercase;
  margin: 8px auto;
}
.btnS{
  width: 80px;
  height: 80px;
  padding: 1em;
  outline: none;
  border: none;
  background-color: purple;
  color: white;
  text-transform: uppercase;
  display: flex; 
  justify-content: center;
  align-items: center;
  margin:  20px auto;
}

.box4{
  display: grid;
  grid-template-columns: repeat(4,250px);
  gap: 20px;
  justify-content: center;

}
}
</style>
