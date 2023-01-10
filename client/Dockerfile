FROM node:16-alpine as builder
WORKDIR "/app"
COPY ./package.json ./
RUN npm install
COPY . .
# build the production version of our front end assets:
RUN npm run build 
# the output of the previous command will be in the /app folder on a file called build 


# nginx:
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/conf 
COPY --from=builder /app/build /usr/share/nginx/html

