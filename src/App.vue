<script>
export default {
  data() {
    return {
      nome: '',
      senha: '',
      menssagem: '',
      problema: '',
      produto: [],
      priemiroProblema: false,
      urgencia: '',
      exibirDiv: true
    }
  },
  methods: {
    ocultarDiv() {
      this.exibirDiv = !this.exibirDiv;
    }
  }
}
</script>

<template>
  <h1>Preenchimento Dinamico</h1>
  <main class="container-form">
    <section>
      <h2>Preencha </h2>
      <span class="view-btn" @click="ocultarDiv">
        <v-icon :icon="exibirDiv ? 'mdi-eye' : 'mdi-eye-off'"></v-icon>
      </span>
      <form action="">
        <v-text-field type="nome" label="Nome" v-model="nome"></v-text-field>
        <v-text-field type="password" label="Senha" v-model="senha"></v-text-field>
        <v-textarea label="Menssagem" v-model="menssagem"></v-textarea>
        <v-radio-group inline label="Caracteristica do problema" v-model="problema">
          <v-radio label="Reproduzivel" value="Reproduzivel" v-model="problema.reproduzivel"></v-radio>
          <v-radio label="Intermitente" value="Intermitente" v-model="problema.intermitente"></v-radio>
        </v-radio-group>
        <div>
          <v-label> Qual produto?</v-label>
          <div class="container-check">
            <v-checkbox label="Web" value="Web" v-model="produto"></v-checkbox>
            <v-checkbox label="Mobile" value="Mobile" v-model="produto"></v-checkbox>
            <v-checkbox label="Outro" value="Outro" v-model="produto"></v-checkbox>
          </div>

        </div>


        <v-autocomplete label="Autocomplete" v-model="urgencia" :items="['Urgente', 'Média', 'Baixa']"></v-autocomplete>
        <v-switch label="Primeiro Problema?" v-model="priemiroProblema" inset></v-switch>
      </form>
    </section>
    <section class="view-form" v-show="exibirDiv">

      <h2>Acompanhe</h2>
      <div class="container-view">
        <v-text-field type="nome" label="Nome" :active="true">{{ nome }}</v-text-field>
        <v-text-field type="password" label="Senha" :active="true">{{ senha }}</v-text-field>
        <v-textarea label="Menssagem" :active="true" :value="menssagem"></v-textarea>
        <v-radio-group inline label="Caracteristica do problema" v-model="problema">
          <v-radio label="Reproduzivel" value="Reproduzivel" v-model="problema.reproduzivel"></v-radio>
          <v-radio label="Intermitente" value="Intermitente" v-model="problema.intermitente"></v-radio>
        </v-radio-group>

        <div>
          <v-label> Qual produto?</v-label>
          <div class="container-check">
            <v-checkbox label="Web" value="Web" v-model="produto"></v-checkbox>
            <v-checkbox label="Mobile" value="Mobile" v-model="produto"></v-checkbox>
            <v-checkbox label="Outro" value="Outro" v-model="produto"></v-checkbox>
          </div>

        </div>

        <v-autocomplete label="Autocomplete" v-model="urgencia" :items="['Urgente', 'Média', 'Baixa']"></v-autocomplete>
        <v-switch label="Primeiro Problema?" v-model="priemiroProblema" inset></v-switch>
      </div>
    </section>
  </main>
</template>

<style scoped lang="scss">
* {
  padding: 0;
  border: 0;
}

h1,
h2 {
  text-align: center;
}

.container-form {
  display: flex;
  align-items: center;

  justify-content: space-around;

  @media (max-width: 630px) {
    flex-direction: column;
  }

  padding: 32px;
  height: 100%;

  form {
    padding: 8px 32px;
  }

  section {
    width: 100%;
    position: relative;

    .view-btn {
      top: 0px;
      right: 50px;
      position: absolute;
    }
  }

  .container-view {
    padding: 8px 32px;
    pointer-events: none;
    opacity: 0.7;
  }

  .container-check {
    display: flex;
    flex-wrap: wrap;

  }


}</style>
