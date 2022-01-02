<template>
  <div id="app">
    <Header />
    <b-container class="mt-5">
      <b-row>
        <SelectUser
          :getUsuarioSelecionado="getUsuarioSelecionado"
          v-show="!flag"
        />
        <b-col md="3" :offset="flag ? 9 : 0">
          <b-button @click="onChangeFlag" variant="success"
            >Novo usuario</b-button
          >
          {{ flag }}
        </b-col>
      </b-row>
      <Card
        v-show="!flag"
        v-if="usuarioSelecionado"
        :nome="usuarioSelecionado.firstName + ' ' + usuarioSelecionado.lastName"
        :idade="Number(usuarioSelecionado.age)"
        :username="usuarioSelecionado.username"
        :password="usuarioSelecionado.password"
        :onChangeFlag="onChangeFlag"
      />

      <b-row v-if="flag">
        <Form :usuarioSelecionado="usuarioSelecionado" />
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import SelectUser from "./components/SelectUser.vue";
import Card from "./components/Card.vue";
import Form from "./components/Form.vue";

export default {
  name: "App",
  components: {
    Header,
    SelectUser,
    Card,
    Form,
  },

  data: function () {
    return {
      usuarioSelecionado: null,
      flag: false,
    };
  },

  methods: {
    getUsuarioSelecionado: function (usuario) {
      this.usuarioSelecionado = usuario;
    },

    onChangeFlag: function () {
      this.flag = !this.flag;
    },
  },
};
</script>

<style>
</style>
