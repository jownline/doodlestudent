#On part de l'image existante ubuntu
FROM ubuntu
#On récupère tous les fichiers de la racine
COPY . .
#installation de java
RUN apt-get update && apt-get install --no-install-recommends -y\
    openjdk-11-jdk
#build du back
RUN ./mvnw package -Dmaven.test.skip=true
#on indique le port sur lequel il devra se lancer
EXPOSE 8080
#runner prêt à démarer
CMD ["java","-jar","taget/tlcdemoApp-runner.jar"]

#Pour créer l'image docker du back, se positionner à la racine /api, puis taper : docker build . -t doodleback -f Dockerfile