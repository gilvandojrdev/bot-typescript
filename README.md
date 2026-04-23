# Guia de Configuração da Aplicação

Este guia define o padrão de inicialização para o desenvolvimento do bot, garantindo que o ambiente TypeScript esteja devidamente sincronizado com o Node.js.

---

## 1. Requisitos de Ambiente

É obrigatória a instalação do Node.js para a execução do projeto. Recomenda-se a versão mais recente para suporte a recursos modernos de módulos.

* Download: https://nodejs.org
* Versão utilizada: `v24.11.1` ou superior

---

## 2. Preparação do Diretório

Execute os comandos abaixo no terminal para inicializar o projeto:

```bash
# Inicializar o gerenciador de pacotes
npm init -y

# Instalar o compilador TypeScript como dependência de desenvolvimento
npm install typescript --save-dev

# Instalar as definições de tipos do Node.js
npm install @types/node --save-dev

# Gerar o arquivo de configuração do TypeScript
npx tsc --init
```

---

## 3. Estrutura do package.json

A configuração abaixo define os scripts de automação e o tipo de módulo do projeto:

```json
{
  "name": "app",
  "version": "1.0.0",
  "main": "dist/index.js",
  "type": "module",
  "scripts": {
    "dev": "ts-node src/index.ts",
    "build": "tsc",
    "start": "npm run build && node dist/index.js"
  },
  "devDependencies": {
    "@types/node": "^22.0.0",
    "ts-node": "^10.9.2",
    "typescript": "^5.0.0"
  }
}
```

---

## 4. Configuração do Compilador (tsconfig.json)

Configuração otimizada para TypeScript 5+ com resolução de módulos moderna:

```json
{
  "compilerOptions": {
    "target": "ESNext",
    "module": "ESNext",
    "lib": ["ESNext"],
    "types": ["node"],
    "moduleResolution": "bundler",
    "moduleDetection": "force",
    "rootDir": "./src",
    "outDir": "./dist",
    "strict": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "forceConsistentCasingInFileNames": true,
    "skipLibCheck": true,
    "skipDefaultLibCheck": true,
    "resolveJsonModule": true,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "importHelpers": true,
    "sourceMap": false,
    "declaration": false
  },
  "include": [
    "src",
    "enviroment.d.ts"
  ],
  "exclude": [
    "node_modules",
    "**/*.spec.ts"
  ]
}
```

---

Este padrão garante consistência no desenvolvimento, compilação e execução do projeto.
