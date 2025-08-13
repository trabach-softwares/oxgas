<template>
  <header class="menu-container">
    <div class="logo-area">
      <img src="../assets/logo.png" alt="OXGAS" class="logo" @click="navigate('Home')" />
    </div>
    
    <!-- Menu Desktop -->
    <nav class="desktop-nav">
      <ul class="menu-list">
        <li><a href="#" @click.prevent="navigate('Home')" :class="{ active: activeView === 'Home' }">Home</a></li>
        <li><a href="#" @click.prevent="navigate('Empresa')" :class="{ active: activeView === 'Empresa' }">Empresa</a></li>
        <li><a href="#" @click.prevent="navigate('Estrutura')" :class="{ active: activeView === 'Estrutura' }">Estrutura</a></li>
        <li><a href="#" @click.prevent="navigate('Produtos')" :class="{ active: activeView === 'Produtos' }">Produtos</a></li>
        <li><a href="#" @click.prevent="navigate('Contato')" :class="{ active: activeView === 'Contato' }">Contato</a></li>
      </ul>
    </nav>
    
    <!-- Botão Hamburger Mobile -->
    <button 
      class="hamburger-button" 
      @click="toggleMobileMenu"
      :class="{ active: isMobileMenuOpen }"
      aria-label="Menu"
    >
      <span class="hamburger-line"></span>
      <span class="hamburger-line"></span>
      <span class="hamburger-line"></span>
    </button>
    
    <!-- Overlay para fechar menu -->
    <div 
      v-if="isMobileMenuOpen" 
      class="menu-overlay" 
      @click="closeMobileMenu"
    ></div>
    
    <!-- Menu Mobile Lateral -->
    <nav class="mobile-nav" :class="{ active: isMobileMenuOpen }">
      <div class="mobile-menu-header">
        <div class="header-content">
          <div class="menu-title">
            <h3>Menu de Navegação</h3>
            <p>OXGAS - Gases Industriais</p>
          </div>
          <!-- BOTÃO X REMOVIDO AQUI -->
        </div>
      </div>
      
      <ul class="mobile-menu-list">
        <li>
          <a 
            href="#" 
            @click.prevent="navigateAndClose('Home')" 
            :class="{ active: activeView === 'Home' }"
          >
            <i class="fas fa-home"></i>
            <span>Home</span>
            <i class="fas fa-chevron-right arrow-icon"></i>
          </a>
        </li>
        <li>
          <a 
            href="#" 
            @click.prevent="navigateAndClose('Empresa')" 
            :class="{ active: activeView === 'Empresa' }"
          >
            <i class="fas fa-building"></i>
            <span>Empresa</span>
            <i class="fas fa-chevron-right arrow-icon"></i>
          </a>
        </li>
        <li>
          <a 
            href="#" 
            @click.prevent="navigateAndClose('Estrutura')" 
            :class="{ active: activeView === 'Estrutura' }"
          >
            <i class="fas fa-industry"></i>
            <span>Estrutura</span>
            <i class="fas fa-chevron-right arrow-icon"></i>
          </a>
        </li>
        <li>
          <a 
            href="#" 
            @click.prevent="navigateAndClose('Produtos')" 
            :class="{ active: activeView === 'Produtos' }"
          >
            <i class="fas fa-box"></i>
            <span>Produtos</span>
            <i class="fas fa-chevron-right arrow-icon"></i>
          </a>
        </li>
        <li>
          <a 
            href="#" 
            @click.prevent="navigateAndClose('Contato')" 
            :class="{ active: activeView === 'Contato' }"
          >
            <i class="fas fa-phone"></i>
            <span>Contato</span>
            <i class="fas fa-chevron-right arrow-icon"></i>
          </a>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: "Menu",
  props: {
    activeView: {
      type: String,
      default: 'Home'
    }
  },
  data() {
    return {
      isMobileMenuOpen: false,
      scrollPosition: 0
    }
  },
  methods: {
    navigate(viewName) {
      this.$emit('navigate', viewName);
    },
    
    navigateAndClose(viewName) {
      this.navigate(viewName);
      this.closeMobileMenu();
    },
    
    toggleMobileMenu() {
      this.isMobileMenuOpen = !this.isMobileMenuOpen;
      this.toggleBodyScroll();
    },
    
    closeMobileMenu() {
      this.isMobileMenuOpen = false;
      this.enableBodyScroll();
    },
    
    toggleBodyScroll() {
      if (this.isMobileMenuOpen) {
        // Salvar posição atual do scroll
        this.scrollPosition = window.pageYOffset || document.documentElement.scrollTop;
        
        // Bloquear scroll e manter posição
        document.body.style.overflow = 'hidden';
        document.body.style.position = 'fixed';
        document.body.style.top = `-${this.scrollPosition}px`;
        document.body.style.width = '100%';
        document.body.classList.add('menu-open');
        
        // Bloquear scroll do html também
        document.documentElement.style.overflow = 'hidden';
      } else {
        this.enableBodyScroll();
      }
    },
    
    enableBodyScroll() {
      // Restaurar scroll
      document.body.style.overflow = '';
      document.body.style.position = '';
      document.body.style.top = '';
      document.body.style.width = '';
      document.body.classList.remove('menu-open');
      document.documentElement.style.overflow = '';
      
      // Restaurar posição do scroll
      if (this.scrollPosition > 0) {
        window.scrollTo(0, this.scrollPosition);
        this.scrollPosition = 0;
      }
    },
    
    handleEscape(e) {
      if (e.key === 'Escape' && this.isMobileMenuOpen) {
        this.closeMobileMenu();
      }
    }
  },
  
  mounted() {
    // Fechar menu ao redimensionar para desktop
    window.addEventListener('resize', () => {
      if (window.innerWidth > 768 && this.isMobileMenuOpen) {
        this.closeMobileMenu();
      }
    });
    
    // Fechar menu com ESC
    document.addEventListener('keydown', this.handleEscape);
  },
  
  beforeUnmount() {
    this.enableBodyScroll();
    document.removeEventListener('keydown', this.handleEscape);
  }
};
</script>

<style src="../styles/Menu.css"></style>
