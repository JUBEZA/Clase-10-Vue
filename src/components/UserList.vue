<template>
  <div>
    <p>UserList</p>
    {{ loading }}
    <div>
      <ul>
        <li v-for="user in users" :key="user.id">{{ user.name }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    name: "UserList",
    data() {
      return{
        loading: false,
        users: [],
      };
    },
    created(){
      this.getUsers()
    },
    methods: {
      getUsers() {
        this.loading = true
        fetch("https://649df2bc9bac4a8e669e7987.mockapi.io/users")
        .then(res => res.json())
        .then((users) => {
            this.users = users;
            this.loading = false;
        });
      },
    },

  };

</script>
