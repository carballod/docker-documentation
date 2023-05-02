# /app /usr /lib
# FROM --platform=linux/amd64 node:19.2-alpine3.16
# FROM --platform=$BUILDPLATFORM node:19.2-alpine3.16
FROM node:19.2-alpine3.16
# /app <- viene con una carpeta interna, ahi se coloca la app

# cd app
WORKDIR /app

# dest /app
COPY package.json ./

# Instalar las dependencias
RUN npm install

# Copiar todo lo que esta en el path y pegarlo en el workdir
COPY . .

# Realizar testing
RUN npm run test

#Eliminar archivos y directorios no necesarios en PROD
RUN rm -rf tests && rm -rf node_modules

# Unicamente instala las dependencias de PROD
RUN npm install --prod

# Comando run de la imagen
CMD [ "node", "app.js" ]