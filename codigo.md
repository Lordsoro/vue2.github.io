<template>
  <div id="app" class="container">
    <div v-for="user in users" :key="user.id">
      <h3>{{ user.username }}</h3>
      <li>{{ user.id }} - {{ user.name }}</li>
    </div>
  </div>
</template>

<script>
export default {
  name: "UsersList",
  data() {
    return {
      users: [],
    };
  },
  methods: {
    created() {
      let text = { name: "gwen" };

      let post = {
        method: "POST",
        body: JSON.stringify(text),
        Headers: {
          contentType: "application/json",
        },
      };
      fetch("https://jsonplaceholder.typicode.com/users", post)
        .then((response) => response.json())
        .then((data) => (this.users = data));
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
  color: black;
}
</style>
