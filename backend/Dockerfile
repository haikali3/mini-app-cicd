# Use Node.js base image
# FROM node:18-alpine
FROM alpine:3.21

# Set working directory
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package.json .

# Install dependencies
RUN pnpm install

# Copy the rest of the application code
COPY . .

# Expose the application port
EXPOSE 3000

# Start the application
CMD ["pnpm", "run", "dev"]
