# React Native build environment
FROM node:18-bullseye

WORKDIR /app
COPY package*.json yarn.lock ./
RUN yarn install

# Install Android SDK (optional: only if building APK)
RUN apt-get update && apt-get install -y openjdk-11-jdk android-sdk

COPY . .

# Run Metro bundler (React Native dev server)
EXPOSE 8081
CMD ["yarn", "start"]
