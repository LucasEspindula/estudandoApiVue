<template>
  <div>
    <h4>Teste de listagem</h4>
    <ul>
      <li v-for="(usuario, index) in users" :key="index">
        {{ usuario.firstName }} {{ usuario.lastName }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "SelectUser",

  data: function () {
    return {
      users: [],
    };
  },

  methods: {
    getUser: async function () {
      const result = await fetch("http://localhost:3000/")
        .then((res) => res.json())
        .then((res) => res)
        .catch((error) => {
          return {
            error: true,
            message: error,
          };
        });

      if (!result.error) {
        this.users = result;
      }
      console.log(result);
    },
  },

  created: function () {
    this.getUser();
  },
};
</script>

<style>
</style>