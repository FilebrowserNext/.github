<p align="center">
  <img src="https://raw.githubusercontent.com/FilebrowserNext/filebrowserNEXT/main/frontend/public/img/logo.svg" width="64" height="64" alt="File Browser Next Logo" />
</p>

<h1 align="center" style="margin-top: 4px; margin-bottom: 4px;">FilebrowserNext</h1>

<p align="center" style="margin-top: 0; margin-bottom: 12px;">
  <b>Building the next generation of open-source, self-hosted file management.</b>
</p>

<p align="center">
  <a href="https://filebrowsernext.github.io/filebrowserNEXT/"><img src="https://img.shields.io/badge/Documentation-GitHub_Pages-6366f1?style=flat-square&logo=gitbook&logoColor=white" alt="Documentation"/></a>
  <a href="https://github.com/FilebrowserNext/filebrowserNEXT/releases/latest"><img src="https://img.shields.io/badge/Release-v3.0.0--next-22c55e?style=flat-square" alt="Latest Release"/></a>
  <a href="https://github.com/orgs/FilebrowserNext/packages/container/package/filebrowsernext"><img src="https://img.shields.io/badge/Docker-GHCR-0ea5e9?style=flat-square&logo=docker&logoColor=white" alt="Docker"/></a>
  <a href="https://github.com/FilebrowserNext/get"><img src="https://img.shields.io/badge/Installer-get.sh-8b5cf6?style=flat-square" alt="Installer"/></a>
  <a href="https://github.com/FilebrowserNext/filebrowserNEXT"><img src="https://img.shields.io/badge/Main_Project-filebrowserNEXT-0ea5e9?style=flat-square&logo=github&logoColor=white" alt="Main Project"/></a>
  <a href="https://github.com/FilebrowserNext/filebrowserNEXT/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-Apache_2.0-22c55e?style=flat-square" alt="License"/></a>
</p>

<p align="center">
  <a href="https://github.com/FilebrowserNext/filebrowserNEXT">
    <img src="https://raw.githubusercontent.com/FilebrowserNext/.github/main/profile/demo.gif" width="680" alt="File Browser Next Live Interactive Demo" style="border-radius: 10px; box-shadow: 0 12px 30px rgba(0,0,0,0.25);" />
  </a>
</p>

---

## What We Build

**FilebrowserNext** is an open-source organization dedicated to maintaining and evolving a modern, secure, self-hosted web file manager.

Our flagship project — **File Browser Next** — is a community-driven continuation of the original File Browser, rebuilt with a focus on security hardening, modern UI, and long-term maintainability.

---

## File Browser Next

> A modern, secure, and self-hosted web-based file manager.

File Browser Next lets you manage files directly from your browser — upload, download, preview, edit, share, and organize — all within your own infrastructure. No cloud dependency, no data leaving your server.

### What Makes It Different

| Feature | File Browser Next | Original File Browser |
|---|---|---|
| Server-side JWT revocation | Yes | No |
| Session invalidation on permission change | Yes | No |
| Brute force protection on login | Yes | No |
| Hardened HTTP security headers | Yes | No |
| Shell injection filtering | Yes | No |
| Case-insensitive login | Yes | No |
| No spurious logouts on preference save | Yes | No (bug) |
| Modern glassmorphic UI | Yes | No |
| Active maintenance | Yes | Archived |

---

## Security First

Security was the primary motivation for this fork. The original project had several open issues that were never resolved:

- **No server-side token revocation** — logging out did not actually invalidate the JWT ([#5216](https://github.com/filebrowser/filebrowser/issues/5216))
- **Command injection vulnerability** — shell metacharacters were not filtered ([#5199](https://github.com/filebrowser/filebrowser/issues/5199))
- **No brute force protection** — the login endpoint had no rate limiting
- **Missing security headers** — no `X-Frame-Options`, `X-Content-Type-Options`, or `Permissions-Policy`

All of these are resolved in File Browser Next, with full unit test coverage.

---

## Quick Start

### 1. Automated 1-Liner Install (Linux & macOS)

```bash
curl -fsSL https://raw.githubusercontent.com/FilebrowserNext/get/main/get.sh | bash
filebrowser -r /path/to/your/files
```

### 2. Docker Run

```bash
docker run -d \
  --name filebrowser \
  --restart unless-stopped \
  -p 8080:80 \
  -v /path/to/your/files:/srv \
  -v /path/to/database:/database \
  ghcr.io/filebrowsernext/filebrowsernext:latest
```

### 3. Build from Source

```bash
git clone https://github.com/FilebrowserNext/filebrowserNEXT.git
cd filebrowserNEXT
pnpm --dir frontend install && pnpm --dir frontend build
go build -o filebrowser .
./filebrowser -r /path/to/your/files
```

Open `http://127.0.0.1:8080` (or `http://<your-server-ip>:8080`) — default credentials: `admin` / `admin`.

---

## Repositories & Links

| Project | Description | Link |
|---|---|---|
| Core Project | Main application codebase and issues | [FilebrowserNext/filebrowserNEXT](https://github.com/FilebrowserNext/filebrowserNEXT) |
| Installer Script | Automated installation scripts (`get.sh`, `get.ps1`) | [FilebrowserNext/get](https://github.com/FilebrowserNext/get) |
| Docker Image | Multi-arch container image on GHCR | [ghcr.io/filebrowsernext/filebrowsernext](https://github.com/orgs/FilebrowserNext/packages/container/package/filebrowsernext) |
| Documentation | Live documentation and deployment guide | [filebrowsernext.github.io/filebrowserNEXT](https://filebrowsernext.github.io/filebrowserNEXT/) |
| Releases | Prebuilt binaries for Linux, macOS, and Windows | [Releases](https://github.com/FilebrowserNext/filebrowserNEXT/releases) |
| Security Policy | Security disclosures and vulnerability reporting | [SECURITY.md](https://github.com/FilebrowserNext/filebrowserNEXT/blob/main/docs/security.md) |

---

<p align="center">
  <sub>File Browser Next Contributors &amp; File Browser Authors — Apache License 2.0</sub>
</p>
