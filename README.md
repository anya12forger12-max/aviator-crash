# Aviator Crash — client UI

A polished React + TypeScript front end for a real-time crash-style game client. This repository contains the browser UI only: it connects to an external API and Socket.IO server through configuration, renders flight/betting state, and hosts the Unity WebGL presentation assets.

> **Scope note:** There is no backend, wallet, payment processor, or game server in this repository. The UI is intended for a simulated/demo environment. Do not connect it to real-money services.

## What is here

- **Real-time game surface** driven by Socket.IO events.
- **Betting panels** for placing bets, tracking active rounds, and cashing out.
- **History views** for all bets, your bets, and top results.
- **Unity WebGL integration** via `react-unity-webgl`, with bundled Unity assets under `public/unity`.
- **Responsive interface** built with React, TypeScript, Tailwind CSS, and SCSS.
- **User feedback** through toasts, spinners, and a loading/progress screen.
- **Smoke test** that verifies the app shell renders.
- **Dependency hardening** through npm overrides, including a patched `elliptic` tarball in `security-patches/`.

## Architecture

```
src/
├── app.tsx              # Root layout, loading/recharge overlays, header + game panels
├── context.tsx          # Shared client state/provider
├── config.ts            # API and WebSocket base URL from REACT_APP_API_URL
├── components/
│   ├── bet-users/       # All bets, my bets, top history tables
│   ├── crash/           # Crash/flight presentation
│   ├── Main/            # Bet controls and round history
│   ├── header.tsx       # Top navigation/balance area
│   └── cTelegram.tsx    # Telegram-related UI helper
└── assets/              # Images and static UI assets
public/unity/            # Unity WebGL build served by this client
```

The client expects a backend that exposes REST endpoints under `/api` and a Socket.IO endpoint at the same origin configured by `REACT_APP_API_URL`.

## Requirements

- Node.js 18 or newer
- npm 9 or newer
- A compatible backend providing the REST + Socket.IO contract expected by the UI

## Configuration

Create a `.env` file in the project root:

```dotenv
REACT_APP_API_URL=https://your-api.example
```

`src/config.ts` derives:

- `api` → `${REACT_APP_API_URL}/api`
- `wss` → `REACT_APP_API_URL`

## Install and run

```bash
npm install
```

Start the development server on port 4000:

```bash
PORT=4000 npx react-app-rewired start
```

Build for production without source maps:

```bash
GENERATE_SOURCEMAP=false npx react-app-rewired build
```

Run the test suite:

```bash
npm test
```

> The scripts in `package.json` use Windows `set PORT=...` syntax. The commands above are cross-platform equivalents for POSIX shells. `npm run start1` and `npm run build1` use plain `react-scripts` without the rewired config.

## Security and responsible use

- This client must **not** receive session tokens through URL query strings; recent hardening captures and scrubs such parameters after load.
- The client must **not** submit a client-computed cash-out target. The authoritative server derives payout from its own game state.
- The patched `elliptic` dependency is vendored in `security-patches/` and pinned through npm `overrides`. Do not remove that override without reviewing the advisory it addresses.
- No real-money functionality is included. Keep this UI in demo/simulation environments unless a licensed operator integration and appropriate controls are added outside this repo.

## Project status

This snapshot is a front-end client with a small smoke test. It does not include a game-server implementation, database models, operator/admin tooling, or documentation for the upstream API contract.

## License

No `LICENSE` file is present in this repository. Unless otherwise stated, all rights are reserved by the repository owner. Contact information from earlier revisions: Discord `cashblaze129`, Telegram `@cashblaze129`, LinkedIn [Keyvel Bitcoin Solana](https://www.linkedin.com/in/keyvel-bitcoin-solana).
