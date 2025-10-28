# ---------- Stage 1: Build ----------
FROM node:18-alpine AS builder

WORKDIR /app
COPY package*.json ./
RUN yarn install
COPY . .
RUN yarn build

# ---------- Stage 2: Run ----------
FROM node:18-alpine

WORKDIR /app
COPY package*.json ./
RUN yarn install --production

# Copy only the compiled code from builder
COPY --from=builder /app/dist ./dist

CMD ["node", "dist/main.js"]
