<template>
  <div class="contato">
    <!-- Fale Conosco -->
    <section class="contact-section">
      <div class="container">
        <div class="contact-content">
          <div class="contact-image">
            <img src="../assets/banner.png" alt="Instalações OXGAS" />
            <div class="image-overlay">
              <div class="overlay-content">
                <i class="fas fa-industry"></i>
                <h3>Excelência em Gases</h3>
                <p>Qualidade e segurança em cada produto</p>
              </div>
            </div>
          </div>
          
          <div class="contact-form-area">
            <div class="form-header">
              <div class="header-icon">
                <i class="fas fa-comments"></i>
              </div>
              <p class="form-subtitle">Possui alguma dúvida, reclamação ou sugestão?</p>
              <h2>Fale Conosco</h2>
            </div>
            
            <form class="contact-form" @submit.prevent="handleSubmit">
              <div class="form-group">
                <label for="name" class="form-label">Nome completo</label>
                <input 
                  id="name"
                  v-model="form.name"
                  type="text" 
                  placeholder="Digite seu nome completo" 
                  required 
                  class="form-input"
                  :class="{ 'error': errors.name, 'success': form.name && !errors.name }"
                />
                <span v-if="errors.name" class="error-message">{{ errors.name }}</span>
              </div>

              <div class="form-group">
                <label for="phone" class="form-label">Telefone</label>
                <input 
                  id="phone"
                  v-model="form.phone"
                  type="tel" 
                  placeholder="(27) 99999-9999" 
                  required 
                  class="form-input"
                  :class="{ 'error': errors.phone, 'success': form.phone && !errors.phone }"
                />
                <span v-if="errors.phone" class="error-message">{{ errors.phone }}</span>
              </div>

              <div class="form-group">
                <label for="email" class="form-label">E-mail</label>
                <input 
                  id="email"
                  v-model="form.email"
                  type="email" 
                  placeholder="seu@email.com" 
                  required 
                  class="form-input"
                  :class="{ 'error': errors.email, 'success': form.email && !errors.email }"
                />
                <span v-if="errors.email" class="error-message">{{ errors.email }}</span>
              </div>

              <div class="form-group">
                <label for="message" class="form-label">Mensagem</label>
                <textarea 
                  id="message"
                  v-model="form.message"
                  placeholder="Descreva sua dúvida, sugestão ou reclamação..." 
                  rows="5" 
                  required 
                  class="form-textarea"
                  :class="{ 'error': errors.message, 'success': form.message && !errors.message }"
                ></textarea>
                <span v-if="errors.message" class="error-message">{{ errors.message }}</span>
              </div>
              
              <button 
                type="submit" 
                class="form-button"
                :class="{ 'loading': isLoading }"
                :disabled="isLoading"
              >
                <span v-if="!isLoading">
                  <i class="fas fa-paper-plane"></i>
                  Enviar Mensagem
                </span>
                <span v-else>
                  <i class="fas fa-spinner fa-spin"></i>
                  Enviando...
                </span>
              </button>

              <div v-if="submitStatus === 'success'" class="success-message">
                <i class="fas fa-check-circle"></i>
                Mensagem enviada com sucesso! Retornaremos em breve.
              </div>

              <div v-if="submitStatus === 'error'" class="error-message">
                <i class="fas fa-exclamation-circle"></i>
                Erro ao enviar mensagem. Tente novamente.
              </div>
            </form>
          </div>
          
          <div class="contact-info">
            <div class="info-section">
              <div class="section-header">
                <i class="fas fa-map-marker-alt"></i>
                <h3>Nossas Unidades</h3>
              </div>
              
              <div class="location-card">
                <div class="location-header">
                  <i class="fas fa-building"></i>
                  <h4>Cariacica-ES</h4>
                </div>
                <div class="contact-item">
                  <i class="fas fa-phone"></i>
                  <span>+ 55 27 3336-1630</span>
                </div>
              </div>
              
              <div class="location-card">
                <div class="location-header">
                  <i class="fas fa-building"></i>
                  <h4>Cachoeiro de Itapemirim-ES</h4>
                </div>
                <div class="contact-item">
                  <i class="fas fa-phone"></i>
                  <span>+ 55 27 3517-8626</span>
                </div>
              </div>
              
              <div class="location-card">
                <div class="location-header">
                  <i class="fas fa-building"></i>
                  <h4>Linhares-ES</h4>
                </div>
                <div class="contact-item">
                  <i class="fas fa-phone"></i>
                  <span>+55 27 3264-4684</span>
                </div>
              </div>
            </div>
            
            <div class="info-section">
              <div class="section-header">
                <i class="fas fa-calculator"></i>
                <h3>Orçamentos</h3>
              </div>
              <div class="contact-item">
                <i class="fas fa-briefcase"></i>
                <div>
                  <strong>Comercial:</strong><br>
                  <span>+ 55 27 99968-1063</span><br>
                  <span>+ 55 27 99968-1016</span>
                </div>
              </div>
              <div class="contact-item">
                <i class="fas fa-envelope"></i>
                <span>vendas@oxgas.com.br</span>
              </div>
            </div>
            
            <div class="social-section">
              <h4>Siga-nos</h4>
              <div class="social-media">
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
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "Contato",
  data() {
    return {
      form: {
        name: '',
        phone: '',
        email: '',
        message: ''
      },
      errors: {},
      isLoading: false,
      submitStatus: null
    }
  },
  methods: {
    validateForm() {
      this.errors = {};
      
      if (!this.form.name.trim()) {
        this.errors.name = 'Nome é obrigatório';
      }
      
      if (!this.form.phone.trim()) {
        this.errors.phone = 'Telefone é obrigatório';
      }
      
      if (!this.form.email.trim()) {
        this.errors.email = 'E-mail é obrigatório';
      } else if (!/\S+@\S+\.\S+/.test(this.form.email)) {
        this.errors.email = 'E-mail inválido';
      }
      
      if (!this.form.message.trim()) {
        this.errors.message = 'Mensagem é obrigatória';
      }
      
      return Object.keys(this.errors).length === 0;
    },
    
    async handleSubmit() {
      if (!this.validateForm()) return;
      
      this.isLoading = true;
      this.submitStatus = null;
      
      try {
        // Simular envio
        await new Promise(resolve => setTimeout(resolve, 2000));
        
        this.submitStatus = 'success';
        this.form = { name: '', phone: '', email: '', message: '' };
      } catch (error) {
        this.submitStatus = 'error';
      } finally {
        this.isLoading = false;
      }
    }
  }
};
</script>

<style src="../styles/Home.css"></style>