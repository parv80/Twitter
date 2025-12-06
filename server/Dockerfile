FROM node:18-alpine

WORKDIR /app

# Copy package files
COPY package*.json ./

# Install only production dependencies
RUN npm install --production

# Copy all source files
COPY . .

# Copy .env file explicitly (required for Docker!)
COPY .env .env

ENV NODE_ENV=production
EXPOSE 3001

CMD ["node", "src/index.js"]
