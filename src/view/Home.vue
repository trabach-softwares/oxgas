<template>
  <div class="home">
    <!-- Banner -->
    <section class="banner">
      <img src="../assets/banner.png" alt="Cilindros" />
    </section>

    <!-- Incluindo todas as seções na Home -->
    <Produtos />
    <Empresa />
    <Contato />
  </div>
</template>

<script>
import Produtos from './Produtos.vue';
import Empresa from './Empresa.vue';
import Contato from './Contato.vue';

export default {
  name: "Home",
  components: {
    Produtos,
    Empresa,
    Contato
  }
};
</script>

<style src="../styles/Home.css"></style>
