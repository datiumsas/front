<template>
    <div>
      <h1>User List</h1>
      <ul>
        <li v-for="user in users" :key="user.id">
          {{ user.firstName }} {{ user.lastName }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios'; // Import Axios library
  
  export default {
    data() {
      return {
        users: [],
      };
    },
    mounted() {
      // Fetch users from the API when the component is mounted
      this.fetchUsers();
    },
    methods: {
      fetchUsers() {
        // Make an API call to retrieve the users
        axios
          .get('http://localhost:4000/user/All')
          .then(response => {
            this.users = response.data;
          })
          .catch(error => {
            console.error(error);
          });
      },
    },
  };
  </script>
  
  <style>
  /* Add your custom styles here */
  </style>
  