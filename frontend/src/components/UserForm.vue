<template>
  <div>
    <h2>Add User</h2>
    <form @submit.prevent="addUser">
      <input v-model="user.name" placeholder="Name" required />
      <input v-model="user.email" placeholder="Email" type="email" required />
      <input v-model="user.password" placeholder="Password" type="password" required />
      <button type="submit">Add</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {
        name: '',
        email: '',
        password: '',
      },
    };
  },
  methods: {
    async addUser() {
      try {
        const response = await fetch('http://localhost:3000/users', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify(this.user),
        });

        if (!response.ok) {
          throw new Error(`Error adding user: ${response.statusText}`);
        }

        this.$emit('refresh');
        this.user = { name: '', email: '', password: '' };
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<style scoped>
form {
  margin-bottom: 20px;
}
input {
  margin: 5px;
  padding: 5px;
}
button {
  margin: 5px;
  padding: 5px 10px;
  cursor: pointer;
}
</style>
