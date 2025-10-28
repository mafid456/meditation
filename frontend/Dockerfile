# ---------- Stage 1: Build ----------
FROM node:18-alpine AS build
WORKDIR /app

COPY package*.json yarn.lock ./
RUN yarn install --frozen-lockfile

COPY . .

# Add a build command for web version
RUN yarn add expo-cli -g && yarn build:web

# ---------- Stage 2: Serve via Nginx ----------
FROM nginx:alpine
COPY --from=build /app/web-build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
