<template>
  <div>RequestOPedia</div>
  <div class="container p-4">
    <div >
      <h1 class="text-success text-center">TravelOpedia</h1>
    </div>
    <hr />
    <table class="table table-striped table-light">
      <thead>
        <tr>
          <th>Name</th>
          <th>Days</th>
          <th>Price</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="destination in destinationObj.destinationList" :key="destination.id">
          <td>{{ destination.name }}</td>
          <td>{{ destination.days }}</td>
          <td>{{ destination.price }}</td>
        </tr>
      </tbody>
    </table>
  </div>

</template>
<script setup>
import axios from "axios";
import { onMounted, reactive } from "vue";

const destinationObj = reactive({
  destinationList: [],
});
onMounted(() => {
  // fetch("https://jsonplaceholder.typicode.com/users")
  //   .then((response) => response.json())
  //   .then((data) => {
  //     console.log(data);
  //     userObj.users = data;
  //   });

  axios.get("http://localhost:3000/destination").then((response) => {
    console.log(response.data);
    destinationObj.destinationList = response.data;
  });
});
</script>
