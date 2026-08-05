<div align="center">

<img src="https://app.olamto.fun/logo.png" width="110" alt="Olamto Logo" style="border-radius: 18px; box-shadow: 0 0 30px rgba(43, 84, 255,0.3);" />

# ⚡ Olamto Studio

### Next-Gen Web3 AI Agentic Platform & Cloudflare One MCP Portals

[![npm version](https://img.shields.io/npm/v/@OlamtoStudio/agents?style=for-the-badge&color=cb3837&logo=npm)](https://www.npmjs.com/package/@OlamtoStudio/agents)
[![GitHub Repo](https://img.shields.io/badge/GitHub-OlamtoStudio%2Fagents-CCFF00?style=for-the-badge&logo=github)](https://github.com/OlamtoStudio/agents)
[![License: MIT](https://img.shields.io/badge/License-MIT-4285F4.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![Robinhood Chain](https://img.shields.io/badge/Robinhood-EVM%204663-CCFF00?style=for-the-badge&logo=ethereum)](https://app.olamto.fun)
[![Solana Network](https://img.shields.io/badge/Solana-MCP%20Autofixer-dc1fff?style=for-the-badge&logo=solana)](https://app.olamto.fun)
[![Cloudflare Edge](https://img.shields.io/badge/Cloudflare-MCP%20Portals-F38020?style=for-the-badge&logo=cloudflare)](https://app.olamto.fun)

[🌐 Live Studio App](https://app.olamto.fun) • [📖 Developer Docs](https://app.olamto.fun/docs) • [🐙 GitHub](https://github.com/OlamtoStudio/agents) • [𝕏 (Twitter)](https://x.com/OlamtoStudio) • [✈️ Telegram](https://t.me/OlamtoStudio)

</div>

---

## 🚀 Overview

**Olamto Studio** is the premier Web3 AI development platform designed for autonomous smart contract engineering, stateful AI agent execution, and Model Context Protocol (MCP) server portals running natively on Cloudflare Workers Edge.

```
                     ┌───────────────────────────────────────────────┐
                     │          Olamto AI Engine Core             │
                     │       (16 Frontier AI Models Suite)           │
                     └───────────────────────┬───────────────────────┘
                                             │
            ┌────────────────────────────────┼────────────────────────────────┐
            ▼                                ▼                                ▼
┌─────────────────────────┐     ┌─────────────────────────┐     ┌─────────────────────────┐
│   Robinhood EVM Chain   │     │  Solana MCP Autofixer   │     │  Cloudflare One MCP     │
│   Solidity Compiler     │     │   Anchor & Pinocchio    │     │  5x Token Savings       │
│   Chain ID 4663         │     │   Rust Program Repair   │     │  Workers Codemode       │
└─────────────────────────┘     └─────────────────────────┘     └─────────────────────────┘
```

---

## ✨ Core Features

* **🤖 Autonomous Agent SDK (`@OlamtoStudio/agents`)**: Event-driven agent base class with edge state persistence via Durable Objects and real-time WebSocket fibers.
* **🟢 Robinhood EVM Chain (Chain ID 4663)**: Native Solidity compilation, static vulnerability auditing via Blockscout API, and gas estimation.
* **🟣 Solana MCP Program Autofixer**: Anchor & Pinocchio Rust smart contract error parsing, IDL generation, and automated code repair.
* **⚡ Cloudflare One MCP Server Portals**: 5x Token Savings optimization via `minimize_tools()` & `search_and_execute()`, reducing context window usage by up to 80%.
* **𝗤 Cloudflare D1 SQL Vault**: Serverless SQL storage for user configurations, API key vaults, and rate limits.

---

## 📦 Installation

Since `@OlamtoStudio/agents` is hosted directly on GitHub, install it directly using npm, yarn, or pnpm:

```bash
# Install directly from GitHub Repository
npm install github:OlamtoStudio/agents

# Using yarn
yarn add OlamtoStudio/agents

# Using pnpm
pnpm add github:OlamtoStudio/agents
```

Or clone and build from source:

```bash
git clone https://github.com/OlamtoStudio/agents.git
cd agents
npm install && npm run build
```

---

## ⚡ Quick Start

Create an autonomous Web3 AI agent in TypeScript:

```typescript
import { Agent, type Connection, type WSMessage, type AgentEnv } from "@OlamtoStudio/agents";

export class Web3AuditorAgent extends Agent {
  constructor(env: AgentEnv) {
    super(env);
  }

  // 1. Triggered on connection establishment
  async onConnect(connection: Connection): Promise<void> {
    console.log("⚡ Olamto Agent booted on Robinhood EVM Chain ID 4663");
    connection.send(JSON.stringify({
      type: "ready",
      status: "Connected to Olamto Studio Edge"
    }));
  }

  // 2. Triggered on incoming message or tool command
  async onMessage(connection: Connection, message: WSMessage): Promise<void> {
    const data = typeof message === "string" ? JSON.parse(message) : message;

    if (data.action === "audit") {
      await this.setState({ last_contract: data.contract });
      const currentState = await this.getState();

      connection.send(JSON.stringify({
        status: "success",
        state: currentState,
        content: `Audit initiated for contract on Robinhood EVM Chain ID 4663`
      }));
    }
  }

  // 3. Triggered when client disconnects
  async onClose(connection: Connection): Promise<void> {
    console.log("Client disconnected:", connection.id);
  }
}
```

---

## 📖 SDK Reference (`@OlamtoStudio/agents`)

### Agent Abstract Base Class

```typescript
import { Agent, type Connection, type WSMessage, type AgentEnv } from "@OlamtoStudio/agents";

export class CustomAgent extends Agent {
  constructor(env: AgentEnv) {
    super(env);
  }

  // Boots up connection context
  async onConnect(connection: Connection): Promise<void> {}

  // Handles incoming messages and tool execution commands
  async onMessage(connection: Connection, message: WSMessage): Promise<void> {}

  // Handles connection teardown
  async onClose(connection: Connection): Promise<void> {}
}
```

### Session State Storage

```typescript
// Set state
await this.setState({ user_wallet: "0x46633e21a4168923058b71b93f21" });

// Get current state
const currentState = await this.getState();
```

---

## ⛓️ Robinhood EVM Chain Integration (Chain ID 4663)

```typescript
import { RobinhoodEVM } from "@OlamtoStudio/agents";

const evm = new RobinhoodEVM({
  rpcUrl: "https://rpc.robinhood.olamto.fun",
  chainId: 4663,
});

const auditResult = await evm.auditContract(`
  pragma solidity ^0.8.20;
  contract OlamtoToken {
      mapping(address => uint256) public balances;
      function transfer(address to, uint256 amount) public {
          balances[msg.sender] -= amount;
          balances[to] += amount;
      }
  }
`);

console.log("Audit Status:", auditResult.status);
console.log("Vulnerabilities:", auditResult.issues);
```

---

## ☀️ Solana MCP Program Autofixer

```typescript
import { SolanaMCP } from "@OlamtoStudio/agents";

const solana = new SolanaMCP();

const fixResult = await solana.autofixProgram({
  sourceCode: rustProgramCode,
  errorMessage: "Error: AccountDiscriminatorMismatch",
});

console.log("Repaired Rust Code:", fixResult.repairedCode);
```

---

## 🌐 Official Channels & Resources

* 🌐 **Live Application**: [https://app.olamto.fun](https://app.olamto.fun)
* 📖 **Developer Documentation**: [https://app.olamto.fun/docs](https://app.olamto.fun/docs)
* 🐙 **GitHub Repository**: [https://github.com/OlamtoStudio/agents](https://github.com/OlamtoStudio/agents)

---

<div align="center">
  <sub>MIT License © 2026 Olamto Foundation</sub>
</div>
