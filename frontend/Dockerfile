# ---------- Stage 1: Build ----------
FROM node:18-alpine AS build

WORKDIR /app

# Copy dependency files first (for better caching)
COPY package*.json yarn.lock ./

# Install dependencies
RUN yarn install --frozen-lockfile

# Copy source code and build
COPY . .
RUN yarn build

# ---------- Stage 2: Serve ----------
FROM nginx:alpine

# Copy compiled app to nginx html directory
COPY --from=build /app/build /usr/share/nginx/html

# Copy custom nginx config (optional)
# COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

