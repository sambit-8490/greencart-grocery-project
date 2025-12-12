# Use Node.js
FROM node:20-alpine

# Set working directory
WORKDIR /app

# Copy package files first (better caching)
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the backend files
COPY . .

# Copy environment file into container
COPY .env ./.env

# Expose backend port
EXPOSE 4000

# Start server
CMD ["node", "server.js"]
