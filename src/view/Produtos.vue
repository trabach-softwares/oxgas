<template>
  <div class="produtos">
    <!-- Cards de Produtos -->
    <section class="cards">
      <div class="card">
        <img src="../assets/icon-gas.png" alt="Gás" />
        <h3>GÁS</h3>
        <p>Gases Industriais, Medicinais, Alimentícios e Especiais.</p>
      </div>
      <div class="card">
        <img src="../assets/icon-equip.png" alt="Equipamentos" />
        <h3>EQUIPAMENTOS</h3>
        <p>Reguladores de Pressão, Oxicorte, Soldas Especiais e Arames.</p>
      </div>
      <div class="card">
        <img src="../assets/icon-service.png" alt="Serviços" />
        <h3>SERVIÇOS</h3>
        <p>Instalação, Manutenção de Redes, Teste Hidrostático e Locação de Cilindros.</p>
      </div>
    </section>

    <!-- Gases que vendemos -->
    <section class="gases-section">
      <div class="container">
        <h2>Gases que vendemos</h2>
        <div class="gases-grid">
          <div class="gas-item">
            <i aria-hidden="true" class="gas-icon fas fa-spinner"></i>
            <div class="gas-content">
              <h3>Gases Industriais</h3>
              <p>Oxigênio, Acetileno, Argônio, Dióxido de Carbono, Nitrogênio, Hélio, Etileno e Misturas para Aplicação em Solda.</p>
            </div>
          </div>
          
          <div class="gas-item">
            <i aria-hidden="true" class="gas-icon fas fa-spinner"></i>
            <div class="gas-content">
              <h3>Gases Criogênicos Líquidos</h3>
              <p>Oxigênio, Argônio, Dióxido de Carbono e Nitrogênio em estado líquido para grandes volumes.</p>
            </div>
          </div>

          <div class="gas-item">
            <i aria-hidden="true" class="gas-icon fas fa-spinner"></i>
            <div class="gas-content">
              <h3>Gases para Corte a Laser</h3>
              <p>Misturas especiais para calibração e processos de corte a laser de alta precisão.</p>
            </div>
          </div>

          <div class="gas-item">
            <i aria-hidden="true" class="gas-icon fas fa-spinner"></i>
            <div class="gas-content">
              <h3>Gases Especiais</h3>
              <p>Produtos específicos desenvolvidos de acordo com a demanda e necessidade do cliente.</p>
            </div>
          </div>

          <div class="gas-item">
            <i aria-hidden="true" class="gas-icon fas fa-spinner"></i>
            <div class="gas-content">
              <h3>Gases Grau Analítico Ultra Puro</h3>
              <p>Argônio, Oxigênio e Hélio com pureza superior para laboratórios e análises técnicas.</p>
            </div>
          </div>

          <div class="gas-item">
            <i aria-hidden="true" class="gas-icon fas fa-spinner"></i>
            <div class="gas-content">
              <h3>Gases Alimentícios</h3>
              <p>Dióxido de Carbono e Etileno para conservação e processamento de alimentos.</p>
            </div>
          </div>

          <div class="gas-item">
            <i aria-hidden="true" class="gas-icon fas fa-spinner"></i>
            <div class="gas-content">
              <h3>Gases Liquefeito do Petróleo</h3>
              <p>P-45, P-20 e P-13 para diversas aplicações industriais e comerciais.</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "Produtos"
};
</script>

<style src="../styles/Home.css"></style>