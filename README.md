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
docker build -t haikali3/mini-app-backend .
docker build -t haikali3/mini-app-frontend .
```

2. Run the Docker container:

```sh
docker run -p 3000:3000 haikali3/mini-app-backend
docker run -p 8000:80 haikali3/mini-app-frontend
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

4. Have fun
