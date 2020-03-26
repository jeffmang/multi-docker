# start with node image and name as builder
FROM node:alpine as builder
# set up default dir for docker container to be /app
WORKDIR "/app"
# copy over package.json
COPY ./package.json ./
# run npm installer
RUN npm install
# copy over everything else
COPY . .
# execute command npm run build - which will output all asset files to /app/build
CMD ["npm", "run", "build"]

# start new image which is nginx
FROM nginx
# make port 3000 available outside the container
EXPOSE 3000
# copy the local default.conf file to the container image
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# copy the output file /app/build in the builder container to the container nginx in the html dir
COPY --from=builder /app/build /usr/share/nginx/html
