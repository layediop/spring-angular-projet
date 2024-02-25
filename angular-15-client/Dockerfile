# Utiliser une image Node.js comme base
FROM node:latest

# Définir le répertoire de travail
WORKDIR /usr/src/app

# Copier les fichiers de package.json et package-lock.json
COPY package*.json ./

# Installer les dépendances
RUN npm install

# Copier les fichiers de l'application
COPY . ./

# Expose le port
EXPOSE 3000

# Commande pour exécuter l'application lorsqu'un conteneur est lancé
CMD [ "npm", "start" ]

