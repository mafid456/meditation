# ---------- Stage 1: Build ----------
FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json yarn.lock ./
RUN yarn install --frozen-lockfile
COPY . .
RUN yarn build

# ---------- Stage 2: Run ----------
FROM node:18-alpine
WORKDIR /app
COPY --from=build /app/dist ./dist
COPY package*.json yarn.lock ./
RUN yarn install --production --frozen-lockfile
EXPOSE 3000
CMD ["node", "dist/main.js"]
