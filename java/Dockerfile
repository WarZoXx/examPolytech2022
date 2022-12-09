FROM maven:3.8-openjdk-8 as builder

#selection du working directory dans le docker
WORKDIR /usr/src/app

# on copie le repertoire courant dans le workdir
COPY . .

run mvn clean package -DskipTests=true

FROM openjdk:8-jdk

# Créateur du docker file
LABEL maintainer="Gaston Maimbourg"

# selection du working directory dans le docker
WORKDIR /usr/src/app

COPY --from=builder /usr/src/app/target/java-*.jar java-back.jar

# défini le port utilisé par le docker
# ca ne remplace pas le mapping qu'il faudra faire au démarage du docker
EXPOSE 8448 

# démarage de l'API
CMD ["java","-jar","java-back.jar"]