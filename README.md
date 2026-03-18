# CodeVASP AI Skills

This repository contains AI Agent Skills designed to assist developers integrating with the **CodeVASP** network.

By adding these skills to your AI assistant (like Claude Code, Cursor, or other agentic AI environments), the AI gains expert domain knowledge on Travel Rule compliance, VASP discovery, transfer authorizations, IVMS101 JSON payload validation, unhosted wallet verification, and blockchain risk screening.

## What These Skills Can Do

Once loaded, you can ask your AI assistant to:
- **Answer general conceptual questions** about the CodeVASP Protocol, IVMS101 standard, unhosted wallet verification, and Uppsala risk screening.
- **Provide JSON payload templates** for asset transfer requests/responses between Natural and Legal persons.
- **Provide functional code samples** in Node.js, Python, Java, and Go for common integration tasks like header generation and payload encryption.
- **Instruct you on how to authorize transfers** and implement the specific API flows.
- **Validate your JSON payloads** against the official IVMS101 JSON Schema to deterministically catch structural errors or missing mandatory fields.
- **Guide unhosted wallet verification** — token issuance, widget rendering, client event handling, and result retrieval.
- **Guide Uppsala risk screening** — wallet address and TXID risk detection with security category and tag interpretation.

## List of Skills

### CodeVASP Core (`skills/codevasp-core`)
Expert guidance on Travel Rule compliance, CodeVASP API integration, and IVMS101 data structures. Covers VASP discovery, transfer authorization, encryption/decryption, and corporate Travel Rule flows. Includes code samples in Node.js, Python, Java, and Go.

### CodeVASP Unhosted Wallet (`skills/codevasp-unhosted-wallet`)
Expert guidance on Unhosted Wallet Verification API integration. Covers wallet ownership verification via cryptographic signature proof (ECDSA secp256k1), widget rendering (Vanilla JS & React), client event handling, and verification result retrieval. Supports ETH, ARBITRUM, BASE, KAIA, MATIC, SOL, and BSC networks.

### CodeVASP Uppsala Screening (`skills/codevasp-uppsala-screening`)
Expert guidance on Uppsala Screening API integration, jointly operated by CodeVASP and Uppsala Security. Covers wallet address risk detection and transaction ID (TXID) risk screening, returning risk levels (`BLACK`, `GRAY`, `WHITE`, `UNKNOWN`) with security tags. Supports 19 chains including BTC, ETH, SOL, and more. **Production environment only.**

## How to Use These Skills

**Option 1: Using Vercel's `npx skills` (Recommended)**
If you use the `vercel-labs/skills` CLI ecosystem for AI agents, you can install each skill by running:
```bash
# Core Travel Rule skill
npx skills add https://github.com/codevasp-lab/codevasp-skills/skills/codevasp-core

# Unhosted Wallet Verification skill
npx skills add https://github.com/codevasp-lab/codevasp-skills/skills/codevasp-unhosted-wallet

# Uppsala Screening skill
npx skills add https://github.com/codevasp-lab/codevasp-skills/skills/codevasp-uppsala-screening
```

**Option 2: Manual Installation**
1. **Clone or Download** this repository to your local machine.
2. **Add it to your AI Environment**:
    * **Claude Code**: You can usually reference the directory or start a session inside the directory. The AI will read the `SKILL.md` file as part of its system prompt initialization.
    * **Other AI Agents**: Import or upload the folder contents. As long as the agent is capable of reading directory structures and system prompt files, it will utilize the `SKILL.md` instructions and read the files in the `references/` directory.

3. **Ask your AI a question**: Try giving your AI a prompt like:
    > "I need to send an asset transfer authorization from a Legal Person to a Natural Person according to CodeVASP. Can you provide the JSON payload and a Node.js snippet for the headers?"

## Folder Architecture

Each skill is built using the "Domain-specific intelligence" pattern:
- **`SKILL.md`**: The brain of the skill. This contains the triggers and the workflow instructions for the AI on *how* to use the references below.
- **`references/`**: The knowledge base.
  - **`guides/`**: Human-readable documentation (e.g., FAQ, IVMS101 guides, dev environment setup, header parameters) outlining the protocol rules.
  - **`api/`**: Detailed API reference endpoints for integration.
  - **`schemas/`**: (Core only) The strict deterministic JSON schema used by the AI to validate your payloads.
  - **`examples/`**: (Core only) Ready-to-use JSON templates for every combination of Natural and Legal person transfers.
  - **`samples/`**: (Core only) Functional code snippets in Node.js, Python, Java, Go for integration logic.

## Safety & "IP Whitelisting" Note

Because these skills operate on a "Fundamentals" approach — loading static schemas, templates, and guides into the agent's context rather than giving the agent direct MCP (Model Context Protocol) API connectivity — your developers can test their code securely. The AI does not require internet access or direct connectivity to your protected APIs to serve as an expert validator.
