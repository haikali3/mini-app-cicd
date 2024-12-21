FROM alpine:3.21

ENV NODE_VERSION 22.12.0

# Set working directory
WORKDIR /usr/src/app

# Install build tools for sqlite3
RUN apk add --no-cache sqlite sqlite-dev

# Install Node.js, npm, and pnpm
RUN apk add --no-cache nodejs npm \
  && npm install -g pnpm

# Copy package.json and package-lock.json
COPY package.json pnpm-lock.yaml ./

# Install dependencies
RUN pnpm install --frozen-lockfile

# Copy the rest of the application code
COPY . .

# Expose the application port
EXPOSE 3000

# Start the application
CMD ["pnpm", "run", "dev"]
