<template>
  <div class="estrutura">
    <section class="structure-hero">
      <div class="container">
        <h1>Nossa Estrutura</h1>
        <p>Conheça nossas instalações e capacidades técnicas para atender suas necessidades com excelência.</p>
      </div>
    </section>

    <section class="structure-content">
      <div class="container">
        <div class="structure-grid">
          <div class="structure-item">
            <div class="structure-icon">
              <i class="fas fa-industry"></i>
            </div>
            <h3>Planta Industrial</h3>
            <p>Instalações modernas e equipadas com tecnologia de ponta para produção e armazenamento de gases com máxima segurança e qualidade.</p>
          </div>

          <div class="structure-item">
            <div class="structure-icon">
              <i class="fas fa-truck"></i>
            </div>
            <h3>Frota de Entrega</h3>
            <p>Veículos especializados para transporte seguro de gases, garantindo pontualidade e integridade dos produtos.</p>
          </div>

          <div class="structure-item">
            <div class="structure-icon">
              <i class="fas fa-shield-alt"></i>
            </div>
            <h3>Sistemas de Segurança</h3>
            <p>Protocolos rigorosos de segurança e sistemas automatizados de monitoramento para garantir operações seguras.</p>
          </div>

          <div class="structure-item">
            <div class="structure-icon">
              <i class="fas fa-users"></i>
            </div>
            <h3>Equipe Especializada</h3>
            <p>Profissionais qualificados e treinados constantemente para oferecer o melhor atendimento e suporte técnico.</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "Estrutura"
};
</script>

<style>
.structure-hero {
  background: linear-gradient(135deg, #00963f 0%, #00b851 100%);
  color: white;
  padding: 4rem 2rem;
  text-align: center;
}

.structure-hero h1 {
  font-size: 3rem;
  margin-bottom: 1rem;
  font-weight: 600;
}

.structure-hero p {
  font-size: 1.2rem;
  max-width: 600px;
  margin: 0 auto;
  opacity: 0.9;
}

.structure-content {
  padding: 4rem 2rem;
  background: #f8f9fa;
}

.structure-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.structure-item {
  background: white;
  padding: 2rem;
  border-radius: 15px;
  text-align: center;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.structure-item:hover {
  transform: translateY(-5px);
}

.structure-icon {
  width: 80px;
  height: 80px;
  background: linear-gradient(135deg, #00963f, #00b851);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.5rem;
  box-shadow: 0 4px 15px rgba(0, 150, 63, 0.3);
}

.structure-icon i {
  font-size: 2rem;
  color: white;
}

.structure-item h3 {
  color: #333;
  font-size: 1.5rem;
  margin-bottom: 1rem;
  font-weight: 600;
}

.structure-item p {
  color: #666;
  line-height: 1.6;
}

@media (max-width: 768px) {
  .structure-hero h1 {
    font-size: 2rem;
  }
  
  .structure-hero p {
    font-size: 1rem;
  }
  
  .structure-content {
    padding: 2rem 1rem;
  }
}
</style>