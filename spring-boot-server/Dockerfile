# Utilisez une image Maven pour construire l'application
FROM maven:3.8.4 AS build

# Définissez le répertoire de travail dans le conteneur
WORKDIR /app

# Copiez les fichiers de configuration Maven pour minimiser le téléchargement des dépendances
COPY pom.xml .
COPY src ./src

# Exécutez la phase de package de Maven pour générer le JAR
RUN mvn clean package -DskipTests

# Utilisez une image Java 11 en tant qu'image de base
FROM adoptopenjdk:11-jre-hotspot

# Définissez le répertoire de travail dans le conteneur
WORKDIR /app

# Copiez le JAR généré à partir de la phase de build
COPY --from=build /app/target/*.jar app.jar

# Exposez le port sur lequel votre application Spring Boot écoute
EXPOSE 8080

# Commande pour exécuter votre application au démarrage du conteneur
CMD ["java", "-jar", "app.jar"]
