#PHASE 1 
FROM node:alpine as builder
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

#Inside the container, the build folder will be place
# in the working dir. So it will be /app/build

#PHASE 2

FROM nginx 
EXPOSE 80
COPY --from=builder /app/build /usr/share/nginx/html

# The container having EXPOSE will be considered by the AWS as the one to deploy