<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { reactive, ref } from 'vue'

const listItems = ref([])

async function getData() {
    const res = await fetch("https://localhost:7260/api/Clients");
    const finalRes = await res.json();
    listItems.value = finalRes;
  }
getData()
</script>

<template>
  <RouterView />
  <h1>Пытаюсь сделать fetch(получилось)</h1>
  <h3>Клиенты</h3>
  
  <div class="client" v-for="item in listItems">
    {{ item.id }} 
    {{ item.surname }} 
    {{ item.patronymic }} 
    {{ item.phoneNumber }}
    {{ item.address }}
  </div> 

  
</template>

<style >

p,h1,h3{
color: rgb(220,220,220);

}
h1{
  padding: 100px;
  height: 10px;
}
h3,p{
  padding-left:400px;
}
body{
  background-color: rgb( 10, 10, 10 );
  }
  .client
  {
    color: rgb(220,220,220);
    padding-left:300px;
  }
</style>