# Use a imagem base do Node.js
FROM node:18-alpine

# Defina o diretório de trabalho
WORKDIR /usr/src/app

# Instale o git
RUN apk add --no-cache git

# Clone o repositório do GitHub
RUN git clone https://github.com/icaroMelo1/personal-wallet.git .

# Instale as dependências
RUN npm install

# Exponha a porta
EXPOSE 3000

# Comando para iniciar o aplicativo
CMD ["npm", "run", "start"]
