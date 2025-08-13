<template>
  <div class="certificados">
    <section class="certificates-hero">
      <div class="container">
        <h1>Certificados e Documentos</h1>
        <p>Acesse nossos certificados, fichas de segurança e documentos técnicos para garantir o uso seguro de nossos produtos.</p>
      </div>
    </section>

    <section class="certificates-content">
      <div class="container">
        <div class="certificates-grid">
          <div class="certificate-item">
            <div class="certificate-icon">
              <i class="fas fa-file-alt"></i>
            </div>
            <h3>FDS (Ficha de Segurança)</h3>
            <p>Fichas de Dados de Segurança com informações detalhadas sobre manuseio, armazenagem e segurança de todos os nossos produtos químicos e gases.</p>
            <button 
              class="download-btn" 
              @click="downloadFDS"
              :disabled="isDownloading"
            >
              <i v-if="!isDownloading" class="fas fa-download"></i>
              <i v-if="isDownloading" class="fas fa-spinner fa-spin"></i>
              {{ isDownloading ? 'Baixando...' : 'Baixar FDS' }}
            </button>
            
            <!-- Indicador de sucesso -->
            <div v-if="downloadSuccess" class="download-success">
              <i class="fas fa-check-circle"></i>
              Download realizado com sucesso!
            </div>
            
            <!-- Indicador de erro -->
            <div v-if="downloadError" class="download-error">
              <i class="fas fa-exclamation-circle"></i>
              Erro ao baixar o arquivo. Tente novamente.
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "Certificados",
  data() {
    return {
      isDownloading: false,
      downloadSuccess: false,
      downloadError: false
    }
  },
  methods: {
    async downloadFDS() {
      // Reset estados
      this.downloadSuccess = false;
      this.downloadError = false;
      this.isDownloading = true;
      
      try {
        // Simular delay de download
        await new Promise(resolve => setTimeout(resolve, 800));
        
        // Caminho correto baseado na estrutura da sua pasta
        const pdfPath = '/documentos/FDS_AR_SINTETICO_MEDICINAL_REV01.pdf';
        
        // Verificar se o arquivo existe antes de tentar baixar
        const response = await fetch(pdfPath, { method: 'HEAD' });
        
        if (!response.ok) {
          throw new Error(`Arquivo não encontrado: ${response.status}`);
        }
        
        // Criar elemento <a> para download
        const link = document.createElement('a');
        link.href = pdfPath;
        link.download = 'FDS-OXGAS-AR_SINTETICO_MEDICINAL_REV01.pdf';
        link.target = '_blank';
        
        // Adicionar ao DOM, clicar e remover
        document.body.appendChild(link);
        link.click();
        document.body.removeChild(link);
        
        // Mostrar sucesso
        this.downloadSuccess = true;
        setTimeout(() => {
          this.downloadSuccess = false;
        }, 3000);
        
      } catch (error) {
        console.error('Erro no download:', error);
        this.downloadError = true;
        this.downloadErrorMessage = error.message || 'Erro ao baixar o arquivo. Tente novamente.';
        setTimeout(() => {
          this.downloadError = false;
        }, 3000);
      } finally {
        this.isDownloading = false;
      }
    }
  }
};
</script>

<style>
.certificates-hero {
  background: linear-gradient(135deg, #00963f 0%, #00b851 100%);
  color: white;
  padding: 4rem 2rem;
  text-align: center;
}

.certificates-hero h1 {
  font-size: 3rem;
  margin-bottom: 1rem;
  font-weight: 600;
}

.certificates-hero p {
  font-size: 1.2rem;
  max-width: 600px;
  margin: 0 auto;
  opacity: 0.9;
}

.certificates-content {
  padding: 4rem 2rem;
  background: #f8f9fa;
}

.certificates-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.certificate-item {
  background: white;
  padding: 2.5rem 2rem;
  border-radius: 15px;
  text-align: center;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  border-top: 4px solid #00963f;
}

.certificate-item:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.certificate-icon {
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

.certificate-icon i {
  font-size: 2rem;
  color: white;
}

.certificate-item h3 {
  color: #333;
  font-size: 1.5rem;
  margin-bottom: 1rem;
  font-weight: 600;
}

.certificate-item p {
  color: #666;
  line-height: 1.6;
  margin-bottom: 2rem;
}

.download-btn {
  background: linear-gradient(135deg, #00963f, #00b851);
  color: white;
  border: none;
  padding: 1rem 2rem;
  border-radius: 10px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin: 0 auto;
  box-shadow: 0 4px 15px rgba(0, 150, 63, 0.3);
  min-width: 150px;
  justify-content: center;
}

.download-btn:hover:not(:disabled) {
  background: linear-gradient(135deg, #00662c, #00963f);
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(0, 150, 63, 0.4);
}

.download-btn:disabled {
  opacity: 0.7;
  cursor: not-allowed;
  transform: none !important;
}

.download-btn i {
  font-size: 1rem;
}

/* Mensagens de feedback */
.download-success,
.download-error {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  margin-top: 1rem;
  padding: 0.75rem 1rem;
  border-radius: 8px;
  font-size: 0.9rem;
  font-weight: 500;
  animation: fadeInUp 0.3s ease;
}

.download-success {
  background: #d4edda;
  color: #155724;
  border: 1px solid #c3e6cb;
}

.download-error {
  background: #f8d7da;
  color: #721c24;
  border: 1px solid #f5c6cb;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Spinner personalizado */
.fa-spinner {
  animation: spin 1s linear infinite;
}

@keyframes spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@media (max-width: 768px) {
  .certificates-hero h1 {
    font-size: 2rem;
  }
  
  .certificates-hero p {
    font-size: 1rem;
  }
  
  .certificates-content {
    padding: 2rem 1rem;
  }
  
  .certificate-item {
    padding: 2rem 1.5rem;
  }
  
  .certificates-grid {
    grid-template-columns: 1fr;
  }
  
  .download-btn {
    width: 100%;
    max-width: 250px;
  }
}

@media (max-width: 480px) {
  .certificates-hero {
    padding: 3rem 1rem;
  }
  
  .certificates-hero h1 {
    font-size: 1.8rem;
  }
  
  .certificate-item {
    padding: 1.5rem 1rem;
  }
  
  .certificate-icon {
    width: 70px;
    height: 70px;
  }
  
  .certificate-icon i {
    font-size: 1.8rem;
  }
  
  .certificate-item h3 {
    font-size: 1.3rem;
  }
  
  .download-btn {
    padding: 0.8rem 1.5rem;
    font-size: 0.9rem;
    width: 100%;
    max-width: 200px;
  }
  
  .download-success,
  .download-error {
    font-size: 0.85rem;
    padding: 0.6rem 0.8rem;
  }
}
</style>