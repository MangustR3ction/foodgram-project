# Сборка приложения
FROM node:13.12.0-alpine as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . ./
RUN npm run build

# Production stage
FROM nginx:1.23.3-alpine
COPY --from=build /app/build /usr/share/nginx/html