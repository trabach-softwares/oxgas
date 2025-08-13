# OXGAS - Site Corporativo

Site institucional da OXGAS desenvolvido com Vue.js 3 e Vite, focado em fornecer informações sobre produtos, serviços e contato da empresa.

## 🚀 Tecnologias Utilizadas

- **Vue.js 3** - Framework JavaScript progressivo
- **Vite** - Build tool moderna e rápida
- **CSS3** - Estilização com design system customizado
- **Font Awesome** - Biblioteca de ícones
- **Design Responsivo** - Otimizado para desktop e mobile

## 📱 Características

- ✅ **Design Responsivo** - Adaptável para todos os dispositivos
- ✅ **Menu Hamburger** - Navegação móvel otimizada
- ✅ **Loading Component** - Componente de carregamento reutilizável
- ✅ **Design System** - Paleta de cores e variáveis CSS organizadas
- ✅ **UX/UI Moderno** - Interface limpa e profissional

## 🎨 Paleta de Cores

- **Primary**: `#00BF63` (Verde OXGAS)
- **Secondary**: `#28a745` 
- **Background**: `#f8f9fa`
- **Text**: `#2c3e50`

## 📂 Estrutura do Projeto

```
src/
├── components/         # Componentes reutilizáveis
│   ├── Menu.vue       # Navegação principal
│   ├── Loading.vue    # Componente de loading
│   └── Footer.vue     # Rodapé
├── view/              # Páginas da aplicação
│   ├── Home.vue       # Página inicial
│   ├── Produtos.vue   # Página de produtos
│   ├── Empresa.vue    # Sobre a empresa
│   ├── Estrutura.vue  # Estrutura da empresa
│   └── Contato.vue    # Formulário de contato
├── styles/            # Estilos CSS organizados
│   ├── Variables.css  # Design system
│   ├── Menu.css      # Estilos do menu
│   ├── Home.css      # Estilos da home
│   └── Footer.css    # Estilos do rodapé
└── assets/           # Imagens e recursos
```

## 🛠️ Instalação e Uso

### Pré-requisitos
- Node.js (versão 14 ou superior)
- npm ou yarn

### Instalação
```bash
# Clone o repositório
git clone [URL_DO_REPOSITORIO]

# Entre na pasta do projeto
cd oxgas

# Instale as dependências
npm install

# Execute o projeto em modo desenvolvimento
npm run dev
```

### Build para Produção
```bash
# Gere os arquivos otimizados para produção
npm run build

# Visualize o build localmente
npm run preview
```

## 📋 Scripts Disponíveis

- `npm run dev` - Inicia o servidor de desenvolvimento
- `npm run build` - Gera build de produção
- `npm run preview` - Visualiza o build de produção

## 🔧 Configuração

O projeto utiliza Vite como bundler e está configurado no arquivo `vite.config.js`.

## 📱 Responsividade

O site é totalmente responsivo com breakpoints otimizados:

- **Mobile**: 320px - 768px
- **Tablet**: 768px - 1024px  
- **Desktop**: 1024px+

### Recursos Mobile
- Menu hamburger lateral (50% da tela)
- Cards responsivos
- Botões otimizados para touch
- Navegação simplificada

## 🎯 Funcionalidades

### Páginas
- **Home**: Banner principal, sobre nós, produtos em destaque
- **Produtos**: Catálogo completo de produtos e serviços
- **Empresa**: História e valores da OXGAS
- **Estrutura**: Informações sobre a infraestrutura
- **Contato**: Formulário e informações de contato

### Componentes
- **Menu**: Navegação responsiva com animações
- **Loading**: Indicador de carregamento com cancelamento
- **Footer**: Rodapé com informações da empresa

## 🚀 Deploy

O projeto está pronto para deploy em qualquer plataforma que suporte sites estáticos:

- Vercel
- Netlify  
- GitHub Pages
- Firebase Hosting

## 📄 Licença

Este projeto é propriedade da OXGAS.

## 🤝 Contribuição

Para contribuir com o projeto:

1. Faça um fork do repositório
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

---

Desenvolvido com ❤️ para OXGAS
