# ---------- Build Stage ----------
FROM node:18-alpine as build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# Build React project
RUN npm run build

# ---------- Production Server ----------
FROM nginx:stable-alpine

# Remove default nginx HTML content
RUN rm -rf /usr/share/nginx/html/*

# Copy built React files
COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
