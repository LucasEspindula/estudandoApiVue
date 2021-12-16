<template>
  <b-row>
    <b-col md="4">
      <b-card :title="nome">
        <b-card-text>
          <p>Idade : {{ idade }}</p>
          <p>Username : {{ username }}</p>
          <p>Password : {{ password }}</p>
        </b-card-text>
      </b-card>
    </b-col>
  </b-row>
</template>

<script>
export default {
  name: "Card",
  props: {
    nome: String,
    idade: Number,
    username: String,
    password: String,
  },
};
</script>

<style>
</style>