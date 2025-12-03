# build stage
FROM node:lts-alpine AS build-stage

#now location
RUN pwd

WORKDIR /app

#pwd in /app
RUN pwd

#check file
RUN ls -lt

COPY package*.json ./

#check package
RUN ls -lt

RUN npm install

COPY . .

#check file
RUN ls -lt

RUN npm run build

# check dist
RUN ls -lt

RUN ls -lt /app/dist

# production stage
FROM nginx:stable-alpine

#check
RUN ls -lt /usr/share/nginx/html

COPY --from=build-stage /app/dist /usr/share/nginx/html

#check 
RUN ls -lt /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

