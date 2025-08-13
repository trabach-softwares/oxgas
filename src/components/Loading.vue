<template>
  <transition name="loading-fade">
    <div v-if="show" class="loading-overlay" @click="handleOverlayClick">
        <div class="loading-spinner">
            <div class="spinner-ring">
                <div class="spinner-circle"></div>
            </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'Loading',
  props: {
    show: {
      type: Boolean,
      default: false
    },
    title: {
      type: String,
      default: 'Carregando...'
    },
    message: {
      type: String,
      default: 'Aguarde enquanto processamos sua solicitação'
    },
    compact: {
      type: Boolean,
      default: false
    },
    cancellable: {
      type: Boolean,
      default: false
    },
    escToCancel: {
      type: Boolean,
      default: false
    },
    showProgress: {
      type: Boolean,
      default: false
    },
    progress: {
      type: Number,
      default: 0,
      validator: value => value >= 0 && value <= 100
    },
    clickToCancel: {
      type: Boolean,
      default: false
    }
  },
  emits: ['cancel'],
  methods: {
    handleOverlayClick() {
      if (this.clickToCancel) {
        this.$emit('cancel');
      }
    },
    
    handleEscape(e) {
      if (e.key === 'Escape' && this.escToCancel && this.show) {
        this.$emit('cancel');
      }
    }
  },
  
  mounted() {
    if (this.escToCancel) {
      document.addEventListener('keydown', this.handleEscape);
    }
  },
  
  beforeUnmount() {
    if (this.escToCancel) {
      document.removeEventListener('keydown', this.handleEscape);
    }
  },

  watch: {
    show(newVal) {
      if (newVal) {
        // Bloquear scroll quando loading aparece
        document.body.style.overflow = 'hidden';
      } else {
        // Restaurar scroll quando loading some
        document.body.style.overflow = '';
      }
    }
  }
};
</script>

<style scoped>
/* === BASE STYLES === */
.loading-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.4); /* Fundo escuro mais claro */
  backdrop-filter: blur(6px);
  z-index: 9999;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  box-sizing: border-box;
}

.loading-container {
  background: white;
  border-radius: 20px;
  padding: 3rem 2.5rem;
  max-width: 400px;
  width: 100%;
  text-align: center;
  position: relative;
  transform: scale(1);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.loading-container.compact {
  padding: 2rem 1.5rem;
  max-width: 300px;
}

/* === SPINNER VERDE === */
.loading-spinner {
  margin-bottom: 2rem;
  display: flex;
  justify-content: center;
}

.spinner-ring {
  position: relative;
  width: 80px;
  height: 80px;
}

.spinner-circle {
  position: absolute;
  width: 100%;
  height: 100%;
  border: 4px solid transparent;
  border-radius: 50%;
  animation: spin 2s cubic-bezier(0.4, 0, 0.2, 1) infinite;
}

/* Todas as cores do spinner em tons de verde */
.spinner-circle:nth-child(1) {
  border-top-color: #00963f; /* Verde principal */
  animation-delay: 0s;
}

.spinner-circle:nth-child(2) {
  border-right-color: #00b851; /* Verde claro */
  animation-delay: 0.15s;
}

.spinner-circle:nth-child(3) {
  border-bottom-color: #007a3e; /* Verde escuro */
  animation-delay: 0.3s;
}

.spinner-circle:nth-child(4) {
  border-left-color: #26d072; /* Verde vibrante */
  animation-delay: 0.45s;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
    opacity: 1;
  }
  50% {
    transform: rotate(180deg);
    opacity: 0.7;
  }
  100% {
    transform: rotate(360deg);
    opacity: 1;
  }
}

/* === CONTENT === */
.loading-content {
  margin-bottom: 1.5rem;
}

.loading-title {
  color: #333;
  font-size: 1.5rem;
  font-weight: 600;
  margin: 0 0 0.75rem 0;
  line-height: 1.3;
}

.loading-message {
  color: #666;
  font-size: 1rem;
  line-height: 1.5;
  margin: 0;
  opacity: 0.9;
}

/* === PROGRESS BAR VERDE === */
.loading-progress {
  margin-top: 1.5rem;
  display: flex;
  align-items: center;
  gap: 1rem;
}

.progress-bar {
  flex: 1;
  height: 8px;
  background: #f0f0f0;
  border-radius: 4px;
  overflow: hidden;
  position: relative;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(135deg, #00963f, #00b851); /* Gradiente verde */
  border-radius: 4px;
  transition: width 0.3s ease;
  position: relative;
}

.progress-fill::after {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
  animation: shimmer 1.5s infinite;
}

@keyframes shimmer {
  0% { left: -100%; }
  100% { left: 100%; }
}

.progress-text {
  font-size: 0.875rem;
  font-weight: 600;
  color: #00963f; /* Texto verde */
  min-width: 40px;
}

/* === CANCEL BUTTON === */
.loading-cancel {
  background: #dc3545;
  color: white;
  border: none;
  border-radius: 10px;
  padding: 0.75rem 1.5rem;
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin: 0 auto;
}

.loading-cancel:hover {
  background: #c82333;
  transform: translateY(-1px);
  box-shadow: 0 4px 12px rgba(220, 53, 69, 0.3);
}

.loading-cancel:active {
  transform: translateY(0);
}

/* === ESCAPE HINT === */
.escape-hint {
  position: absolute;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  color: rgba(255, 255, 255, 0.8);
  font-size: 0.875rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  background: rgba(0, 0, 0, 0.3);
  padding: 0.5rem 1rem;
  border-radius: 20px;
  backdrop-filter: blur(10px);
}

.escape-hint i {
  font-size: 1rem;
}

/* === TRANSITIONS === */
.loading-fade-enter-active {
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.loading-fade-leave-active {
  transition: all 0.25s ease-in;
}

.loading-fade-enter-from {
  opacity: 0;
  backdrop-filter: blur(0px);
}

.loading-fade-enter-from .loading-container {
  transform: scale(0.9) translateY(20px);
  opacity: 0;
}

.loading-fade-leave-to {
  opacity: 0;
  backdrop-filter: blur(0px);
}

.loading-fade-leave-to .loading-container {
  transform: scale(0.95) translateY(-10px);
  opacity: 0;
}

/* === RESPONSIVIDADE === */

/* Tablet */
@media (max-width: 768px) {
  .loading-overlay {
    padding: 1.5rem;
    background: rgba(0, 0, 0, 0.35); /* Fundo ainda mais claro em mobile */
    backdrop-filter: blur(4px);
  }
  
  .loading-container {
    padding: 2.5rem 2rem;
    max-width: 350px;
    border-radius: 16px;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.12);
  }
  
  .loading-container.compact {
    padding: 2rem 1.5rem;
    max-width: 280px;
  }
  
  .spinner-ring {
    width: 70px;
    height: 70px;
  }
  
  .loading-title {
    font-size: 1.3rem;
  }
  
  .loading-message {
    font-size: 0.95rem;
  }
  
  .escape-hint {
    bottom: 1.5rem;
    font-size: 0.8rem;
    padding: 0.4rem 0.8rem;
  }
}

/* Mobile */
@media (max-width: 480px) {
  .loading-overlay {
    padding: 1rem;
    background: rgba(0, 0, 0, 0.3); /* Fundo bem claro em mobile pequeno */
    backdrop-filter: blur(3px);
  }
  
  .loading-container {
    padding: 2rem 1.5rem;
    max-width: 300px;
    border-radius: 12px;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  }
  
  .loading-container.compact {
    padding: 1.5rem 1rem;
    max-width: 250px;
  }
  
  .spinner-ring {
    width: 60px;
    height: 60px;
  }
  
  .loading-title {
    font-size: 1.2rem;
  }
  
  .loading-message {
    font-size: 0.9rem;
  }
  
  .loading-progress {
    margin-top: 1rem;
    flex-direction: column;
    gap: 0.5rem;
  }
  
  .progress-text {
    align-self: center;
  }
  
  .loading-cancel {
    padding: 0.6rem 1.2rem;
    font-size: 0.85rem;
  }
  
  .escape-hint {
    bottom: 1rem;
    font-size: 0.75rem;
    padding: 0.3rem 0.6rem;
  }
}

/* Mobile Small */
@media (max-width: 360px) {
  .loading-container {
    padding: 1.5rem 1rem;
    max-width: 280px;
    box-shadow: 0 6px 15px rgba(0, 0, 0, 0.08);
  }
  
  .loading-container.compact {
    padding: 1.2rem 0.8rem;
    max-width: 220px;
  }
  
  .spinner-ring {
    width: 50px;
    height: 50px;
  }
  
  .loading-title {
    font-size: 1.1rem;
  }
  
  .loading-message {
    font-size: 0.85rem;
  }
  
  .loading-cancel {
    padding: 0.5rem 1rem;
    font-size: 0.8rem;
  }
}

/* Landscape Mobile */
@media (max-width: 768px) and (orientation: landscape) {
  .loading-overlay {
    padding: 1rem;
    background: rgba(0, 0, 0, 0.35);
  }
  
  .loading-container {
    padding: 1.5rem;
    max-width: 320px;
  }
  
  .spinner-ring {
    width: 50px;
    height: 50px;
  }
  
  .loading-title {
    font-size: 1.1rem;
    margin-bottom: 0.5rem;
  }
  
  .loading-message {
    font-size: 0.85rem;
  }
  
  .escape-hint {
    bottom: 0.5rem;
    font-size: 0.7rem;
  }
}

/* Touch improvements */
@media (pointer: coarse) {
  .loading-cancel {
    min-height: 44px;
    min-width: 120px;
  }
}

/* Reduzir animações para acessibilidade */
@media (prefers-reduced-motion: reduce) {
  .spinner-circle {
    animation: none;
    border: 4px solid #00963f; /* Apenas verde quando sem animação */
  }
  
  .progress-fill::after {
    animation: none;
  }
  
  .loading-fade-enter-active,
  .loading-fade-leave-active {
    transition: opacity 0.2s ease;
  }
  
  .loading-container {
    transition: none;
  }
}

/* Dark mode support */
@media (prefers-color-scheme: dark) {
  .loading-overlay {
    background: rgba(0, 0, 0, 0.6); /* Fundo um pouco mais escuro no dark mode */
  }
  
  .loading-container {
    background: #2d2d2d;
    box-shadow: 0 15px 35px rgba(0, 0, 0, 0.4);
  }
  
  .loading-title {
    color: #f0f0f0;
  }
  
  .loading-message {
    color: #cccccc;
  }
  
  .progress-bar {
    background: #404040;
  }
}

/* Alto contraste */
@media (prefers-contrast: high) {
  .loading-overlay {
    background: rgba(0, 0, 0, 0.7);
  }
  
  .loading-container {
    border: 2px solid #00963f; /* Borda verde apenas em alto contraste */
  }
  
  .loading-title {
    color: #000;
  }
  
  .loading-message {
    color: #333;
  }
}
</style>