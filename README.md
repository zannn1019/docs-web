# 🌐 Website Documentation

> **Note**  
> This website is built using [Docusaurus](https://docusaurus.io/), a modern static website generator optimized for content-rich websites like documentation portals.

---

## 📦 Installation

### 🔧 Option 1: Local Environment (using Yarn)

Make sure you have [Node.js](https://nodejs.org/) and [Yarn](https://yarnpkg.com/) installed.

```bash
yarn install
```

### 🐳 Option 2: Using Docker (Development Mode with Hot Reload)

```bash
docker build -t docusaurus-dev --target dev .
docker run --rm -it -p 3000:3000   -v $(pwd):/opt/docusaurus   docusaurus-dev
```

> This mounts your local project folder and enables hot reloading during development.

---

## 🚀 Local Development

```bash
yarn start
```

This command starts a local development server and opens up your default browser.  
Most changes are hot-reloaded live.

> Or using Docker:
>
> ```bash
> docker run --rm -it -p 3000:3000 -v $(pwd):/opt/docusaurus docusaurus-dev
> ```

---

## 🛠️ Build for Production

```bash
yarn build
```

This command builds the static site and outputs it to the `build/` directory.

> Or using Docker:
>
> ```bash
> docker build -t docusaurus-prod --target prod .
> docker create --name extract docusaurus-prod
> docker cp extract:/opt/docusaurus/build ./build
> docker rm extract
> ```

---

## 🌍 Serve Production Build

### 📦 Option 1: Docusaurus Internal Server

```bash
yarn serve
```

Or using Docker:

```bash
docker build -t docusaurus-serve --target serve .
docker run --rm -it -p 3000:3000 docusaurus-serve
```

### 🌐 Option 2: Serve with Caddy

Make sure you have a valid `Caddyfile` in the project root:

```caddyfile
:3000 {
  root * /var/docusaurus
  file_server
}
```

Then run:

```bash
docker build -t docusaurus-caddy --target caddy .
docker run --rm -it -p 3000:3000 docusaurus-caddy
```

---

## 📤 Deployment

### Using SSH:

```bash
USE_SSH=true yarn deploy
```

### Using GitHub token:

```bash
GIT_USER=<Your GitHub username> yarn deploy
```

> This builds and pushes your website to the `gh-pages` branch for GitHub Pages hosting.

---

## 🧹 Clean Project

```bash
yarn clean
```

Removes `build/`, `node_modules/`, and cache files.

---

## 📁 Directory Overview

```txt
.
├── build/               # Static build output (after running yarn build)
├── docs/                # Markdown docs content
├── src/                 # Custom React components and pages
├── static/              # Static assets (images, files)
├── docusaurus.config.js # Site configuration
└── Dockerfile           # Multi-stage Docker build
```

---

## 📄 License

MIT License © [Your Name or Organization]