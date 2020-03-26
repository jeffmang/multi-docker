FROM node:alpine
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
# run the start script from out package.json file
CMD ["npm", "run", "start"]