# Mini App Backend

This is the backend for the Mini App, built with Node.js and SQLite.

## Prerequisites

- Docker
- Node.js (version 22.12.0)
- pnpm

## Getting Started

### Running with Docker

1. Build the Docker image:

```sh
docker build -t mini-app-backend .
```

2. Run the Docker container:

```sh
docker run -p 3000:3000 mini-app-backend
```

### Running Locally

1. Clone the repository:

```sh
git clone https://github.com/yourusername/mini-app-backend.git
cd mini-app-backend
```

2. Install dependencies:

```sh
pnpm install
```

3. Start the application:

```sh
pnpm run dev
```
