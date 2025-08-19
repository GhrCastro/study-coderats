FROM node:20-alpine

# Diretório de trabalho
WORKDIR /usr/src/app

# Copia package.json se existir, evita erro caso ainda não exista
COPY package*.json ./
RUN npm install || echo "Nenhum package.json encontrado, pulando npm install"

# Copia o restante do código (mesmo que esteja vazio)
COPY . .

EXPOSE 3000

CMD ["sh"]
