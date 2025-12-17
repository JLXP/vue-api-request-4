<template>
  <div>RequestOPedia</div>
  <hr />
  <div v-for="user in userObj.users" :key="user.id">
    <h2>{{ user.name }}</h2>
    <p>{{ user.email }}</p>
    <hr />
  </div>
</template>
<script setup>
import axios from "axios";
import { onMounted, reactive } from "vue";

const userObj = reactive({
  users: [],
});
onMounted(() => {

  fetch("https://jsonplaceholder.typicode.com/users")
    .then((response) => response.json())
    .then((data) => {
      console.log(data);
      userObj.users = data;
    });

  // axios.get("https://jsonplaceholder.typicode.com/users").then((response) => {
  //   console.log(response.data);
  //   userObj.users = response.data;
  // });
});
</script>
