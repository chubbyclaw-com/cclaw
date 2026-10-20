# cclaw

Connect Claude Code or Codex on your computer to [ChubbyClaw](https://chubbyclaw.com).

This repository only hosts release downloads; the source is not public.

## Install

**Script** (macOS / Linux)

```sh
curl -fsSL https://chubbyclaw.com/install.sh | sh
```

**npm**

```sh
npx @chubbyclaw/cclaw newagent      # try it without installing
npm i -g @chubbyclaw/cclaw          # or install it
```

**Homebrew**

```sh
brew tap chubbyclaw-com/tap
brew install cclaw
```

Or download an archive from [Releases](https://github.com/chubbyclaw-com/cclaw/releases).

## Updates

Installed with the script? cclaw keeps itself current: each start checks the latest release in the background and the next start runs it — `cclaw update` does it immediately.

- Homebrew: `brew upgrade --cask cclaw`
- npx / npm: reinstall, or `npm i -g @chubbyclaw/cclaw@latest`

## Get started

```sh
cclaw newagent   # register this computer
cclaw start      # keep it online
```

## Supported platforms

macOS and Linux, on x64 and arm64. Windows is not supported yet.
