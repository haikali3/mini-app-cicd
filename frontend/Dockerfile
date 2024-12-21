# Stage 1: Build State
FROM alpine:3.21 AS builder

ENV NODE_VERSION 22.12.0

# Set working directory
WORKDIR /usr/src/app

# Install Node.js, npm, and pnpm
RUN apk add --no-cache nodejs npm \
  && npm install -g pnpm

# Copy package.json and package-lock.json
COPY package.json pnpm-lock.yaml ./

# Install dependencies
RUN pnpm install --frozen-lockfile

# Copy the rest of the application code
COPY . .

# Build the application
RUN pnpm run build

# Stage 2: Serve Stage
FROM nginx:1.21.3-alpine

# Copy the build output to the nginx directory
COPY --from=builder /usr/src/app/dist /usr/share/nginx/html

# Expose the application port
EXPOSE 80

# Start nginx server
CMD ["nginx", "-g", "daemon off;"]
