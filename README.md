# 🎄 Christmas Terminal Card

![Vue.js](https://img.shields.io/badge/vuejs-%2335495e.svg?style=for-the-badge&logo=vuedotjs&logoColor=%234FC08D)
![Vite](https://img.shields.io/badge/vite-%23646CFF.svg?style=for-the-badge&logo=vite&logoColor=white)
![Netlify](https://img.shields.io/badge/netlify-%2300C7B7.svg?style=for-the-badge&logo=netlify&logoColor=white)

Um cartão de Natal digital e interativo, fugindo dos padrões estáticos. O projeto simula uma interface de terminal (CLI) que "executa scripts natalinos", toca música e finaliza com uma revelação de foto em estilo Polaroid.

Focado em **UX**, **Performance** e **Clean Code**.

---

## ✨ Features

- **Terminal Emulator:** Efeito de digitação (Typewriter) realista com cursor piscante.
- **Cinematic Transitions:** Transições suaves (CSS Keyframes) entre o terminal e a foto.
- **Mobile First:** Totalmente responsivo, com ajustes finos para notch de iPhones e scroll automático.
- **Atmosphere:** Efeitos visuais de CRT (TV antiga), scanlines e neve caindo.
- **Audio Autoplay Handler:** Tela inicial "Click-to-start" para garantir a execução do áudio em navegadores modernos.
- **Easy Config:** Todo o conteúdo (textos, tempos, mídia) centralizado em um único arquivo de configuração.

## 🚀 Tecnologias

- [Vue 3](https://vuejs.org/) (Composition API & Script Setup)
- [Vite](https://vitejs.dev/)
- CSS3 Moderno (Flexbox, Animations, Gradients)
- Google Fonts (Fira Code & Dancing Script)

## 📦 Instalação e Uso

1. **Clone o repositório**
   ```bash
   git clone [https://github.com/SEU-USUARIO/christmas-card-vue.git](https://github.com/SEU-USUARIO/christmas-card-vue.git)
   cd christmas-card-vue

    ```

2. **Instale as dependências**
```bash
npm install

```


3. **Rode localmente**
```bash
npm run dev

```


4. **Build para produção**
```bash
npm run build
# O resultado estará na pasta /dist

```



## ⚙️ Personalização

O projeto foi arquitetado para ser facilmente editável através do arquivo `src/config.js`. Você não precisa mexer na lógica dos componentes.

### 1. Arquivos de Mídia

Coloque seus arquivos na pasta `public/`:

* Sua foto: `public/foto.png`
* Sua música: `public/musica.mp3`

### 2. Editando Textos e Configurações

Abra o arquivo `src/config.js`:

```javascript
export const config = {
  nomeAssinatura: "Seu Nome",
  fotoFamilia: "/foto.png", // Nome do arquivo na pasta public
  musicaFundo: "/musica.mp3",
  
  velocidadeDigitacao: 50, // Menor = Mais rápido
  pausaEntreLinhas: 600,
  
  mensagensTerminal: [
    "> Conectando ao servidor...",
    "Sua mensagem personalizada aqui...",
    "> system.clear()"
  ]
}

```
---
Feito com 🎄 e 💻 por <a href="https://www.google.com/search?q=https://github.com/Arthur1220">Arthur</a>