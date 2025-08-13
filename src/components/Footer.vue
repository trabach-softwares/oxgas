<template>
  <footer class="footer">
    <div class="footer-content">
      <!-- Seção principal do footer -->
      <div class="footer-main">
        <div class="footer-column">
          <div class="footer-logo">
            <img src="../assets/logo.png" alt="OXGAS" class="logo" />
            <!-- <h3>OXGAS</h3> -->
          </div>
          <p class="footer-description">
            Desde 2008, oferecendo gases industriais, medicinais e especiais 
            com excelência e segurança para nossos clientes.
          </p>
          <div class="social-links">
            <a href="#" aria-label="Facebook" class="social-link facebook">
              <i class="fab fa-facebook-f"></i>
            </a>
            <a href="#" aria-label="Instagram" class="social-link instagram">
              <i class="fab fa-instagram"></i>
            </a>
            <a href="#" aria-label="LinkedIn" class="social-link linkedin">
              <i class="fab fa-linkedin-in"></i>
            </a>
          </div>
        </div>

        <div class="footer-column">
          <h4>Navegação</h4>
          <ul class="footer-links">
            <li><a href="#home">Home</a></li>
            <li><a href="#empresa">Empresa</a></li>
            <li><a href="#estrutura">Estrutura</a></li>
            <li><a href="#produtos">Produtos</a></li>
            <li><a href="#contato">Contato</a></li>
          </ul>
        </div>

        <div class="footer-column">
          <h4>Produtos</h4>
          <ul class="footer-links">
            <li><a href="#gases-industriais">Gases Industriais</a></li>
            <li><a href="#gases-medicinais">Gases Medicinais</a></li>
            <li><a href="#equipamentos">Equipamentos</a></li>
            <li><a href="#servicos">Serviços</a></li>
          </ul>
        </div>

        <div class="footer-column">
          <h4>Unidades</h4>
          <div class="contact-info">
            <div class="location">
              <h5>Cariacica-ES</h5>
              <p>
                <i class="fas fa-phone"></i>
                (27) 3336-1630
              </p>
            </div>
            <div class="location">
              <h5>Cachoeiro de Itapemirim-ES</h5>
              <p>
                <i class="fas fa-phone"></i>
                (27) 3517-8626
              </p>
            </div>
            <div class="location">
              <h5>Linhares-ES</h5>
              <p>
                <i class="fas fa-phone"></i>
                (27) 3264-4684
              </p>
            </div>
          </div>
        </div>

        <div class="footer-column">
          <h4>Contato Comercial</h4>
          <div class="commercial-info">
            <p>
              <i class="fas fa-phone"></i>
              (27) 99968-1063
            </p>
            <p>
              <i class="fas fa-phone"></i>
              (27) 99968-1016
            </p>
            <p>
              <i class="fas fa-envelope"></i>
              vendas@oxgas.com.br
            </p>
          </div>
          
          <div class="certifications">
            <h5>Certificações</h5>
            <p class="cert-text">
              <i class="fas fa-certificate"></i>
              Padrão ABNT
            </p>
          </div>
        </div>
      </div>
    </div>

    <!-- Rodapé inferior -->
    <div class="footer-bottom">
      <div class="footer-bottom-content">
        <p>&copy; {{ currentYear }} OXGAS - Todos os direitos reservados.</p>
        <div class="footer-links-bottom">
          <a href="">Desenvolvido por Trabach Softwares</a>
          
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer",
  computed: {
    currentYear() {
      return new Date().getFullYear();
    }
  }
};
</script>

<style src="../styles/Footer.css"></style>