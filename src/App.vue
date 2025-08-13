<template>
  <div id="app">
    <Menu @navigate="handleNavigation" :active-view="currentView" />
    
    <!-- Novo componente Loading -->
    <Loading 
      :show="isLoading"
      :title="loadingTitle"
      :message="loadingMessage"
      :compact="false"
      :cancellable="false"
      :esc-to-cancel="true"
      @cancel="cancelLoading"
    />
    
    <main class="main-content">
      <transition name="fade" mode="out-in">
        <component :is="currentView" :key="currentView" />
      </transition>
    </main>
    
    <Footer />
  </div>
</template>

<script>
import Menu from "../src/components/Menu.vue";
import Loading from "../src/components/Loading.vue";
import Home from "../src/view/Home.vue";
import Empresa from "../src/view/Empresa.vue";
import Estrutura from "../src/view/Estrutura.vue";
import Produtos from "../src/view/Produtos.vue";
import Certificados from "../src/view/Certificados.vue";
import Contato from "../src/view/Contato.vue";
import Footer from "../src/components/Footer.vue";

export default {
  name: "App",
  components: {
    Menu,
    Loading,
    Home,
    Empresa,
    Estrutura,
    Produtos,
    Certificados,
    Contato,
    Footer
  },
  data() {
    return {
      currentView: 'Home',
      isLoading: false,
      loadingTitle: 'Carregando...',
      loadingMessage: 'Preparando o conteúdo para você'
    }
  },
  methods: {
    async handleNavigation(viewName) {
      if (this.currentView !== viewName && !this.isLoading) {
        this.isLoading = true;
        this.loadingTitle = `Carregando ${viewName}`;
        this.loadingMessage = 'Aguarde enquanto preparamos o conteúdo';
        
        try {
          // Simula carregamento
          await new Promise(resolve => setTimeout(resolve, 500));
          
          this.currentView = viewName;
        } catch (error) {
          console.error('Erro na navegação:', error);
        } finally {
          this.isLoading = false;
        }
      }
    },

    cancelLoading() {
      this.isLoading = false;
    }
  }
};
</script>

<style>
/* Reset e estilos globais */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body {
  height: 100%;
}

#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  font-family: 'Montserrat', sans-serif;
  background: #fff;
  position: relative;
}

.main-content {
  flex: 1;
}

/* Container global */
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

/* Reset de estilos para listas */
ul, ol {
  margin: 0;
  padding: 0;
}

/* Links globais */
a {
  color: inherit;
  text-decoration: none;
}

/* Botões globais */
button {
  font-family: inherit;
  cursor: pointer;
}

/* Imagens responsivas */
img {
  max-width: 100%;
  height: auto;
}

/* Smooth scroll */
html {
  scroll-behavior: smooth;
}

/* Foco acessível */
*:focus {
  outline: 2px solid #00963f;
  outline-offset: 2px;
}

/* Seleção de texto */
::selection {
  background: #00963f;
  color: white;
}

/* Transições de página */
.fade-enter-active {
  transition: opacity 0.3s ease-in;
}

.fade-leave-active {
  transition: opacity 0.2s ease-out;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-to,
.fade-leave-from {
  opacity: 1;
}

/* Scrollbar personalizada */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #f1f1f1;
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(135deg, #00963f, #00b851);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(135deg, #00662c, #00963f);
}

/* Reduzir movimento para acessibilidade */
@media (prefers-reduced-motion: reduce) {
  .fade-enter-active,
  .fade-leave-active {
    transition: none;
  }
  
  * {
    transition: none !important;
    animation: none !important;
  }
}

/* Otimizações para mobile */
@media (max-width: 768px) {
  .container {
    padding: 0 0.5rem;
  }
}
</style>
