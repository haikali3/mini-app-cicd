<script>
import UserForm from './components/UserForm.vue';
import UserList from './components/UserList.vue';

export default {
  components: {
    UserForm,
    UserList,
  },
  data() {
    return {
      users: [],
    };
  },
  methods: {
    async fetchUsers() {
      try {
        const response = await fetch('http://localhost:3000/users');
        if (!response.ok) {
          throw new Error(`Error fetching users: ${response.statusText}`);
        }
        this.users = await response.json();
      } catch (error) {
        console.error(error);
      }
    },
  },
  mounted() {
    this.fetchUsers();
  },
};
</script>

<template>
  <div id="app">
    <h1>User Management</h1>
    <UserForm @refresh="fetchUsers" />
    <UserList :users="users" @refresh="fetchUsers" />
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
