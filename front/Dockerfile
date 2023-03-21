#étape durant laquelle on build l'application 
#on part d'une image node disponible sur docker hub

# FROM node:16.13.0 as build-stage
FROM node:10-alpine as build-stage

#on définit le dossier de travail
WORKDIR /app
#on copie le package.json dans le dossier de travail
COPY package.json /app
#on installe toutes les dépendances du package.json
RUN npm install
#on copie les fichiers de la racine dans le répertoire de travail
COPY . /app
#on build l'application et on enregistre le résultat dans le dossier ./dist/out
RUN npm run build -- --outputPath=./dist/out

# On met le résultat de la compilation ci-dessus dans un serveur nginx depuis une image nginx fournie par le docker hub
FROM nginx 
# on récupère le résultat du build (de la compilation) et on le met dans le dossier html du serveur nginx
COPY --from=build-stage /app/dist/out /usr/share/nginx/html

#Pour exécuter ce script permettant d'avoir une image docker, se positionner à la racine du projet et taper : docker build . -t doodlefront -f Dockerfile