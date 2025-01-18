# TiqueTaqueAI

TiqueTaqueAI é um aplicativo de temporizador desenvolvido com Vue 3, TypeScript e Tailwind CSS. Ele oferece funcionalidades de cronômetro e temporizador com contagem regressiva.

## Tecnologias Utilizadas

- Vue 3
- TypeScript
- Tailwind CSS
- Vite

## Requisitos do Sistema

- Node.js (versão 18 ou superior)
- npm (versão 9 ou superior)

## Como Executar Localmente

1. Clone o repositório:
```bash
git clone https://github.com/felipebossolani/TiqueTaqueAI.git
```

2. Instale as dependências:
```bash
cd TiqueTaqueAI
npm install
```

3. Execute o servidor de desenvolvimento:
```bash
npm run dev
```

4. Acesse o aplicativo no navegador:
```
http://localhost:5173
```

## Acesso via GitHub Pages

O aplicativo está disponível online em:
[https://felipebossolani.github.io/TiqueTaqueAI/](https://felipebossolani.github.io/TiqueTaqueAI/)

## Estrutura do Projeto

```
TiqueTaqueAI/
├── src/
│   ├── assets/          # Arquivos estáticos
│   ├── components/      # Componentes Vue
│   ├── App.vue          # Componente principal
│   └── main.ts          # Ponto de entrada
├── public/              # Arquivos públicos
├── tailwind.config.js   # Configuração do Tailwind
├── vite.config.ts       # Configuração do Vite
└── package.json         # Dependências e scripts
```

## Funcionalidades

- Cronômetro com controle de iniciar/parar/zerar
- Temporizador com contagem regressiva
- Interface responsiva e moderna
- Tipagem TypeScript para melhor segurança do código

## Artigos Relacionados

- [Automatizando Frontend com Cline](https://dev.to/felipebossolani/automatizando-frontend-com-cline-299a) - Blog post detalhando o desenvolvimento deste projeto

## Deploy Automático

O projeto está configurado com GitHub Actions para deploy automático na branch `gh-pages` sempre que houver alterações na branch `main`.
