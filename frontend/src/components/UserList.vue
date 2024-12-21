<template>
  <div>
    <h2>User List</h2>
    <ul>
      <li v-for="user in users" :key="user.id">
        {{ user.name }} - {{ user.email }}
        <button @click="deleteUser(user.id)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['users'],
  methods: {
    async deleteUser(id) {
      try {
        const response = await fetch(`http://localhost:3001/users/${id}`, {
          method: 'DELETE',
        });

        if (!response.ok) {
          throw new Error(`Error deleting user: ${response.statusText}`);
        }

        this.$emit('refresh');
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<style scoped>
h2 {
  color: #42b983;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 10px 0;
}
button {
  margin-left: 10px;
  padding: 5px 10px;
  cursor: pointer;
}
</style>
