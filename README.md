<div align="center">

# Awesome Agentic Memory

[![Awesome](https://awesome.re/badge-flat2.svg)](https://awesome.re)
[![Stars](https://img.shields.io/github/stars/aviskaar/awesome-agentic-memory?style=flat-square&color=gold&label=Stars)](https://github.com/aviskaar/awesome-agentic-memory/stargazers)
[![Forks](https://img.shields.io/github/forks/aviskaar/awesome-agentic-memory?style=flat-square&color=blue)](https://github.com/aviskaar/awesome-agentic-memory/network/members)
[![Contributors](https://img.shields.io/github/contributors/aviskaar/awesome-agentic-memory?style=flat-square&color=green)](https://github.com/aviskaar/awesome-agentic-memory/graphs/contributors)
[![Last Commit](https://img.shields.io/github/last-commit/aviskaar/awesome-agentic-memory?style=flat-square)](https://github.com/aviskaar/awesome-agentic-memory/commits/main)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](CONTRIBUTING.md)
[![License: CC0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg?style=flat-square)](LICENSE)

**The most comprehensive curated list of memory systems, plugins, frameworks, databases, and research for AI agents — across coding, chip design, pharma, healthcare, space exploration, smart agriculture, climate science, and every other domain.**

*If your agent forgets everything after a session, this list is your cure.*

[Memory Frameworks](#-memory-frameworks--libraries) · [MCP Servers](#-mcp-memory-servers) · [Agent Frameworks](#-agent-frameworks-with-memory) · [Coding Agents](#-coding-agent-memory-tools) · [Vector DBs](#-vector-databases) · [Knowledge Graphs](#-knowledge-graphs) · [RAG](#-rag-frameworks) · [Industry Verticals](#-industry-verticals) · [Research](#-research-papers) · [Benchmarks](#-benchmarks--evaluation)

</div>

---

## Contents

- [Why Agentic Memory Matters](#-why-agentic-memory-matters)
- [Memory Framework Comparison](#-memory-framework-comparison)
- [Memory Frameworks & Libraries](#-memory-frameworks--libraries)
- [MCP Memory Servers](#-mcp-memory-servers)
- [Agent Frameworks with Memory](#-agent-frameworks-with-memory)
- [Coding Agent Memory Tools](#-coding-agent-memory-tools)
- [Vector Databases](#-vector-databases)
- [Knowledge Graphs](#-knowledge-graphs)
- [RAG Frameworks](#-rag-frameworks)
- [Production / Session Storage](#-production--session-storage)
- [Industry Verticals](#-industry-verticals)
  - [Chip Design & Semiconductors](#chip-design--semiconductors)
  - [Pharmaceutical & Drug Discovery](#pharmaceutical--drug-discovery)
  - [Healthcare & Clinical AI](#healthcare--clinical-ai)
  - [Finance & Trading](#finance--trading)
  - [Legal & Compliance](#legal--compliance)
  - [Manufacturing & Industrial IoT](#manufacturing--industrial-iot)
  - [Scientific Research & Labs](#scientific-research--labs)
  - [Autonomous Vehicles & Robotics](#autonomous-vehicles--robotics)
  - [Education & Tutoring](#education--tutoring)
  - [Space Research & Exploration](#space-research--exploration)
  - [Smart Agriculture & Livestock](#smart-agriculture--livestock)
  - [Climate Science & Environmental Monitoring](#climate-science--environmental-monitoring)
  - [Defense & Intelligence](#defense--intelligence)
  - [Energy & Utilities](#energy--utilities)
- [Research Papers](#-research-papers)
- [Benchmarks & Evaluation](#-benchmarks--evaluation)
- [Awesome Paper Collections](#-awesome-paper-collections)
- [Learning Resources](#-learning-resources)
- [Contributing](#-contributing)

---

## 🧠 Why Agentic Memory Matters

Without memory, every AI agent interaction starts from zero. With the right memory layer, agents can:

- **Remember users** across sessions, building personalized context over time
- **Accumulate knowledge** from past tasks, errors, and successes
- **Reason over time** — understand how facts have changed
- **Coordinate** in multi-agent systems with shared working memory
- **Scale** to production without ballooning token costs

The field has exploded in 2024–2026: from research papers to funded startups to production-grade open-source infrastructure. This list covers all of it.

---

## 📊 Memory Framework Comparison

| Framework | Stars | Memory Types | Backend | MCP | Use Case |
|---|---|---|---|---|---|
| [mem0](#mem0) | ~48k | semantic + episodic + KG | multi-store | ✅ | Universal drop-in |
| [Letta](#letta-formerly-memgpt) | ~15k | virtual context + core + archival | Letta server | ✅ | Long-running stateful agents |
| [Graphiti (Zep)](#graphiti-by-zep) | ~24k | temporal knowledge graph | Neo4j/FalkorDB/Kuzu | ✅ | Real-time temporal memory |
| [Cognee](#cognee) | ~3k | vector + graph + KV | multi-backend | ✅ | 6-line memory setup |
| [LangMem](#langchain--langmem) | bundled | semantic + episodic + procedural | LangGraph Store | ✅ | LangChain/LangGraph agents |
| [Supermemory](#supermemory) | growing | vector + full-text | cloud/local | ✅ | Universal cross-LLM memory |
| [OMEGA](#omega-memory) | growing | structured + semantic | SQLite | ✅ (25 tools) | Coding agents |
| [Hindsight](#hindsight) | growing | 4-network biomimetic | custom | ❌ | High-accuracy retrieval |
| [A-MEM](#a-mem) | growing | Zettelkasten + dynamic | ChromaDB | ❌ | Interconnected knowledge nets |
| [claude-mem](#claude-mem) | growing | conversation + semantic | SQLite | ✅ (Claude Code) | Claude Code sessions |

---

## 🗄️ Memory Frameworks & Libraries

### mem0

[![GitHub Stars](https://img.shields.io/github/stars/mem0ai/mem0?style=flat-square)](https://github.com/mem0ai/mem0)
[![PyPI Downloads](https://img.shields.io/pypi/dm/mem0ai?style=flat-square&label=PyPI)](https://pypi.org/project/mem0ai/)

> Universal memory layer combining vector search, knowledge graphs, and key-value storage. **14M+ downloads. $24M Series A. AWS chose it as the exclusive memory provider for their Agent SDK.**

- **GitHub**: https://github.com/mem0ai/mem0
- **Docs**: https://docs.mem0.ai
- **Memory types**: Semantic, episodic, user-level, agent-level, session-level
- **Backends**: Pinecone, Qdrant, Chroma, Weaviate, Neo4j, and 20+ more

```python
from mem0 import Memory

m = Memory()
m.add("I prefer TypeScript over Python for backend work", user_id="alice")
results = m.search("programming preferences", user_id="alice")
# Returns: [{"memory": "Prefers TypeScript over Python for backend", "score": 0.95}]
```

---

### Letta (formerly MemGPT)

[![GitHub Stars](https://img.shields.io/github/stars/letta-ai/letta?style=flat-square)](https://github.com/letta-ai/letta)

> OS-inspired virtual memory management for LLMs. Agents maintain core memory (always in context), archival memory (infinite recall), and recall memory (conversation history). The original paper introduced the OS analogy for LLM memory.

- **GitHub**: https://github.com/letta-ai/letta
- **Paper**: [MemGPT: Towards LLMs as Operating Systems](https://arxiv.org/abs/2310.08560)
- **Agent file format**: `.af` — portable, shareable agent state
- **Related**: [awesome-letta](https://github.com/letta-ai/awesome-letta) · [agent-file](https://github.com/letta-ai/agent-file)

```python
from letta import create_client

client = create_client()
agent = client.create_agent(name="my_agent")
# Agent remembers context across sessions automatically
response = client.send_message(agent_id=agent.id, message="My name is Alice")
response2 = client.send_message(agent_id=agent.id, message="What's my name?")
# Returns: "Your name is Alice."
```

---

### Graphiti (by Zep)

[![GitHub Stars](https://img.shields.io/github/stars/getzep/graphiti?style=flat-square)](https://github.com/getzep/graphiti)

> Temporal knowledge graph engine where every fact has a validity window. Crossed 20k stars in under 12 months. Outperforms MemGPT on the Deep Memory Retrieval (DMR) benchmark. Has an MCP Server 1.0.

- **GitHub**: https://github.com/getzep/graphiti
- **Paper**: [Zep: A Temporal Knowledge Graph Architecture](https://arxiv.org/abs/2501.13956)
- **Backends**: Neo4j, FalkorDB, Kuzu, Amazon Neptune
- **Latency**: Sub-200ms retrieval
- **MCP**: ✅ Graphiti MCP Server 1.0

```python
from graphiti_core import Graphiti

graphiti = Graphiti(neo4j_uri, neo4j_user, neo4j_password)
await graphiti.add_episode(
    name="user_preference",
    episode_body="Alice said she prefers TypeScript and dislikes Python for APIs",
    source_description="chat session"
)
results = await graphiti.search("Alice programming preferences")
```

---

### Cognee

[![GitHub Stars](https://img.shields.io/github/stars/topoteretes/cognee?style=flat-square)](https://github.com/topoteretes/cognee)

> ECL (Extract, Cognify, Load) pipeline that combines vector + graph search. Memory in 6 lines of code. **$7.5M seed backed by OpenAI and FAIR founders.** Graduated from GitHub Secure Open Source Program.

- **GitHub**: https://github.com/topoteretes/cognee
- **Docs**: https://docs.cognee.ai

```python
import cognee

await cognee.add("Alice is a senior engineer who joined in 2023")
await cognee.cognify()
results = await cognee.search("Tell me about Alice")
```

---

### A-MEM (Agentic Memory)

[![GitHub Stars](https://img.shields.io/github/stars/agiresearch/A-mem?style=flat-square)](https://github.com/agiresearch/A-mem)

> Dynamic memory organization following **Zettelkasten principles** — creates interconnected knowledge networks. NeurIPS 2025. Agents can dynamically index, link, and evolve memory structures.

- **GitHub**: https://github.com/agiresearch/A-mem
- **Paper**: [A-MEM: Agentic Memory for LLM Agents](https://arxiv.org/abs/2502.12110) (NeurIPS 2025)
- **Backend**: ChromaDB

---

### Supermemory

[![GitHub Stars](https://img.shields.io/github/stars/supermemoryai/supermemory?style=flat-square)](https://github.com/supermemoryai/supermemory)

> Claims **#1 on LongMemEval, LoCoMo, and ConvoMem benchmarks**. Extremely fast and scalable. Works across all LLMs with no login required via the MCP server.

- **GitHub**: https://github.com/supermemoryai/supermemory
- **MCP**: https://github.com/supermemoryai/supermemory-mcp
- **Benchmark**: Built [MemoryBench](https://github.com/supermemoryai/supermemory) — open-source framework comparing memory providers

---

### OMEGA Memory

[![GitHub Stars](https://img.shields.io/github/stars/omega-memory/omega-memory?style=flat-square)](https://github.com/omega-memory/omega-memory)

> Persistent memory for AI coding agents. **25 MCP tools.** SQLite backend. Auto-capture and auto-surface. Fully local, zero cloud. Claimed 95.4% on LongMemEval.

- **GitHub**: https://github.com/omega-memory/omega-memory
- **MCP Tools**: 25 tools including memory capture, search, consolidation, timeline
- **Backend**: SQLite (fully local)

---

### Hindsight

[![GitHub Stars](https://img.shields.io/github/stars/vectorize-io/hindsight?style=flat-square)](https://github.com/vectorize-io/hindsight)

> Biomimetic **4-network architecture** (world facts, experiences, entity summaries, evolving beliefs). **91.4% on LongMemEval** with open-source 20B model.

- **GitHub**: https://github.com/vectorize-io/hindsight
- **Paper**: [Hindsight is 20/20](https://arxiv.org/abs/2512.12818)

---

### Memoripy

[![GitHub Stars](https://img.shields.io/github/stars/caspianmoon/memoripy?style=flat-square)](https://github.com/caspianmoon/memoripy)

> Python library with short/long-term storage, semantic clustering, optional memory decay, and graph-based associations. Supports OpenAI, Azure OpenAI, OpenRouter, Ollama.

- **GitHub**: https://github.com/caspianmoon/memoripy

---

### MemOS (Memory Operating System)

> OS-inspired memory management for LLMs. Multiple active implementations. Redis Streams scheduling, multi-modal memory, persistent skill memory.

- **Coding agents**: https://github.com/MemTensor/MemOS
- **EMNLP 2025 Oral**: https://github.com/BAI-LAB/MemoryOS
- **Flexible memory management**: https://github.com/agiresearch/MemOS
- **Paper**: [MemOS: An OS for Memory-Augmented Generation](https://arxiv.org/abs/2505.22101)

---

### ReMe (AgentScope)

> Memory Management Kit for Agents — "Remember Me, Refine Me." Token-aware memory management with work memory + personal memory. From **Alibaba's AgentScope team**. Apache 2.0.

- **GitHub**: https://github.com/agentscope-ai/ReMe

---

### Memori

> SQL-native memory layer for LLMs, AI Agents, and multi-agent systems.

- **GitHub**: https://github.com/MemoriLabs/Memori

---

### SimpleMem

> Efficient lifelong memory for LLM agents with minimal overhead.

- **GitHub**: https://github.com/aiming-lab/SimpleMem

---

### General Agentic Memory (GAM)

> Modular agentic file system framework for structured memory. Supports text and video modalities. Python SDK + CLI + REST API + Web Platform.

- **GitHub**: https://github.com/VectorSpaceLab/general-agentic-memory

---

### MemVid

> Single-file memory layer. Sub-5ms local retrieval. **+35% SOTA on LoCoMo**. Append-only, portable format.

- **GitHub**: https://github.com/memvid/memvid
- **Docs**: https://docs.memvid.com

---

## 🔌 MCP Memory Servers

[Model Context Protocol (MCP)](https://modelcontextprotocol.io) has become the standard for plugging memory into AI tools. Every major memory framework now ships an MCP server.

| Server | Stars | Backend | Tools | Works With |
|---|---|---|---|---|
| [Official MCP Memory](#official-mcp-memory-server) | N/A | JSON file | 9 | Any MCP client |
| [mem0 MCP](#mem0-mcp) | growing | mem0 cloud/local | 4 | Claude, Cursor, any |
| [claude-mem](#claude-mem) | growing | SQLite | 5 hooks | Claude Code |
| [OMEGA MCP](#omega-memory) | growing | SQLite | 25 | Claude Code, Cursor |
| [Graphiti MCP](#graphiti-by-zep) | ~24k | Neo4j/FalkorDB | 8 | Claude, Cursor |
| [Supermemory MCP](#supermemory) | growing | cloud | 4 | Any MCP client |
| [Redis Agent Memory](#redis-agent-memory-server) | growing | Redis | 6 | Any MCP client |
| [mcp-memory-service](#mcp-memory-service) | growing | KG + vector | 12 | Claude, LangGraph |
| [memory-bank-mcp](#memory-bank-mcp) | growing | file system | 8 | Cline, Cursor |
| [neo4j agent memory MCP](#neo4j-agent-memory) | growing | Neo4j | 6 | Any MCP client |
| [kuzu-memory-graph-mcp](#kuzu-memory-graph-mcp) | growing | Kuzu | 5 | Any MCP client |
| [Lockstep](#lockstep) | 10 | Postgres decision ledger | 14 | Claude Code, Cursor, any MCP agent |

---

### Official MCP Memory Server

> Reference implementation from the MCP team. Knowledge graph-based persistent memory stored in a configurable JSON file. 9 tools: `create_entities`, `add_observations`, `search_nodes`, `open_nodes`, and more.

- **GitHub**: https://github.com/modelcontextprotocol/servers/tree/main/src/memory
- **Config**: Set `MEMORY_FILE_PATH` env var to persist across sessions

```json
{
  "mcpServers": {
    "memory": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-memory"],
      "env": { "MEMORY_FILE_PATH": "/path/to/memory.json" }
    }
  }
}
```

---

### mem0 MCP

> Wraps the full mem0 memory API as an MCP server. Works with Claude Desktop, Cursor, Windsurf, and any MCP client.

- **GitHub**: https://github.com/mem0ai/mem0-mcp

```json
{
  "mcpServers": {
    "mem0": {
      "command": "uvx",
      "args": ["mem0-mcp"],
      "env": { "MEM0_API_KEY": "your-key" }
    }
  }
}
```

---

### claude-mem

> Claude Code plugin that **auto-captures everything Claude does**, compresses with AI, and injects relevant context into future sessions. 5 lifecycle hooks. SQLite + semantic search.

- **GitHub**: https://github.com/thedotmack/claude-mem
- **Docs**: https://docs.claude-mem.ai
- **Install**: `claude mcp add claude-mem`

---

### mcp-memory-service

> Open-source persistent memory for AI agent pipelines (LangGraph, CrewAI, AutoGen) and Claude. REST API + knowledge graph + autonomous consolidation. 12 MCP tools.

- **GitHub**: https://github.com/doobidoo/mcp-memory-service

---

### memory-bank-mcp

> MCP server for remote memory bank management, inspired by **Cline Memory Bank**. Persistent structured context for coding sessions.

- **GitHub**: https://github.com/alioshr/memory-bank-mcp

---

### Redis Agent Memory Server

> Fast and flexible memory for agents using Redis. Working memory with auto-TTL, long-term promotion, background compaction. MCP server interface.

- **GitHub**: https://github.com/redis/agent-memory-server

---

### neo4j agent memory MCP

> Memory management MCP server for AI agents using **Neo4j knowledge graphs**. Three memory types: short-term conversation, long-term entity KG, reasoning traces with provenance.

- **GitHub**: https://github.com/knowall-ai/mcp-neo4j-agent-memory

---

### kuzu-memory-graph-mcp

> High-performance LLM memory server using **Kuzu** graph database with semantic search. In-process, sub-3ms recall.

- **GitHub**: https://github.com/jkear/kuzu-memory-graph-mcp

---
---

### Lockstep

> Shared decision memory for teams building with AI coding agents. Captures decisions once, ranks them by blast radius, and briefs every MCP agent before it acts.

- **GitHub**: https://github.com/lockstep-team-agent/lockstep
- **Website**: https://getlockstep.dev
- **Install**: `npm i -g lockstep-cli`


## 🤖 Agent Frameworks with Memory

### LangChain + LangMem

[![GitHub Stars](https://img.shields.io/github/stars/langchain-ai/langmem?style=flat-square)](https://github.com/langchain-ai/langmem)

> LangChain's official agent memory library. Extracts facts from conversations, optimizes prompts over time, maintains long-term memory via LangGraph's Store.

- **LangMem**: https://github.com/langchain-ai/langmem
- **Memory Agent**: https://github.com/langchain-ai/memory-agent
- **LangGraph Memory**: https://github.com/langchain-ai/langgraph-memory
- **Backends**: InMemoryStore, PostgreSQL (pgvector), MongoDB, Redis

```python
from langmem import create_manage_memory_tool, create_search_memory_tool
from langgraph.store.memory import InMemoryStore

store = InMemoryStore()
manage_memory = create_manage_memory_tool(namespace=("user", "alice"))
search_memory = create_search_memory_tool(namespace=("user", "alice"))
```

---

### AutoGPT

[![GitHub Stars](https://img.shields.io/github/stars/Significant-Gravitas/AutoGPT?style=flat-square)](https://github.com/Significant-Gravitas/AutoGPT)

> The original autonomous agent framework. Goal-driven agents with Pinecone-backed vector memory. Modular memory components for file, Redis, and in-memory storage.

- **GitHub**: https://github.com/Significant-Gravitas/AutoGPT
- **Stars**: ~177k

---

### CrewAI

[![GitHub Stars](https://img.shields.io/github/stars/crewAIInc/crewAI?style=flat-square)](https://github.com/crewAIInc/crewAI)

> Role-playing multi-agent framework with a **unified Memory class** in OSS 1.0. Four built-in memory types: short-term (ChromaDB + RAG), long-term (SQLite), entity, and procedural.

- **GitHub**: https://github.com/crewAIInc/crewAI

```python
from crewai import Crew, Agent, Task

crew = Crew(
    agents=[...],
    tasks=[...],
    memory=True,           # Enable all memory types
    verbose=True
)
```

---

### Microsoft AutoGen

[![GitHub Stars](https://img.shields.io/github/stars/microsoft/autogen?style=flat-square)](https://github.com/microsoft/autogen)

> Microsoft's framework for agentic AI workflows. Pluggable memory components. Being merged with Semantic Kernel into the **Microsoft Agent Framework**.

- **GitHub**: https://github.com/microsoft/autogen

---

### Agno (formerly Phidata)

[![GitHub Stars](https://img.shields.io/github/stars/agno-agi/agno?style=flat-square)](https://github.com/agno-agi/agno)

> Production AI agent framework. Claims **5000x faster instantiation than LangGraph**. Built-in session management, long-term user learning storage, 100+ integrations.

- **GitHub**: https://github.com/agno-agi/agno
- **Stars**: ~38k

```python
from agno.agent import Agent
from agno.memory.v2 import Memory
from agno.storage.sqlite import SqliteStorage

agent = Agent(
    memory=Memory(db=SqliteStorage(table_name="agent_memory")),
    add_history_to_messages=True,
    num_history_runs=5,
)
```

---

### Mastra

[![GitHub Stars](https://img.shields.io/github/stars/mastra-ai/mastra?style=flat-square)](https://github.com/mastra-ai/mastra)

> **TypeScript** AI agent framework from the Gatsby team. YC W25, $13M funding. Memory across sessions with libSQL and Postgres backends. 300k+ weekly npm downloads.

- **GitHub**: https://github.com/mastra-ai/mastra

```typescript
import { Memory } from "@mastra/memory";
import { LibSQLStore } from "@mastra/libsql";

const memory = new Memory({
  storage: new LibSQLStore({ url: "file:./memory.db" }),
  options: { lastMessages: 20, semanticRecall: { topK: 5 } }
});
```

---

### MetaGPT

[![GitHub Stars](https://img.shields.io/github/stars/geekan/MetaGPT?style=flat-square)](https://github.com/geekan/MetaGPT)

> Multi-agent framework that simulates software development roles. Shared memory across agent roles (PM, architect, engineer, QA).

- **GitHub**: https://github.com/geekan/MetaGPT
- **Stars**: ~50k

---

### Haystack (deepset)

[![GitHub Stars](https://img.shields.io/github/stars/deepset-ai/haystack?style=flat-square)](https://github.com/deepset-ai/haystack)

> Open-source AI orchestration framework with explicit memory control. `InMemoryChatMessageStore`, `Mem0MemoryStore` integration. RAG + agentic workflows.

- **GitHub**: https://github.com/deepset-ai/haystack

---

### Flowise

[![GitHub Stars](https://img.shields.io/github/stars/FlowiseAI/Flowise?style=flat-square)](https://github.com/FlowiseAI/Flowise)

> **Visual** AI agent builder with 100+ LLM and vector DB integrations. Conversational agents with built-in memory management via drag-and-drop.

- **GitHub**: https://github.com/FlowiseAI/Flowise

---

### Swarms

> Enterprise-grade production-ready multi-agent orchestration. Agent = LLM + Tools + Memory.

- **GitHub**: https://github.com/kyegomez/swarms

---

### AgentVerse

> Facilitates deployment of multiple LLM-based agents. Task-solving and simulation frameworks with shared memory.

- **GitHub**: https://github.com/OpenBMB/AgentVerse

---

### Julep

> Deploy serverless AI workflows. Stateful interactions, persistent memory. (Note: hosted service shut down Dec 2025; self-host works.)

- **GitHub**: https://github.com/julep-ai/julep

---

## 💻 Coding Agent Memory Tools

Memory tools specifically designed for AI coding assistants and developer workflows. Every major AI coding tool now has a memory ecosystem — from built-in context files to MCP plugins to cross-IDE memory layers.

### Quick Reference: Memory Support by Tool

| Tool | Built-in Memory File | MCP Support | Cross-session | Native Memory |
|---|---|---|---|---|
| Claude Code | `CLAUDE.md` (3-tier) | ✅ | ✅ (via plugins) | ✅ Auto-memory |
| OpenCode | `AGENTS.md` | ✅ | ✅ (via plugins) | ❌ |
| OpenAI Codex CLI | `AGENTS.md` | ✅ | ❌ native | ✅ SDK sessions |
| Gemini CLI | `GEMINI.md` | ✅ | ✅ (ADK) | ✅ Conductor ext |
| Kimi CLI | `AGENTS.md` | ✅ | ✅ sessions | ✅ K2.5 native |
| Cursor | `.cursor/rules` | ✅ | ✅ (via MCP) | ❌ |
| Windsurf | Rules files | ✅ | ✅ Cascade Memories | ✅ Auto-memories |
| Aider | `CONVENTIONS.md` | ✅ | ❌ | ❌ |
| Continue.dev | `.continuerc.json` | ✅ | ✅ (via MCP) | ❌ |
| Cline | Custom instructions | ✅ | ✅ Memory Bank | ❌ |

---

### Claude Code

[![Docs](https://img.shields.io/badge/docs-code.claude.com-blue?style=flat-square)](https://code.claude.com/docs/en/memory)

> Anthropic's official CLI for Claude. Three-tier file memory + hook system + rich plugin ecosystem. A well-structured `CLAUDE.md` reduces corrections by ~40% and achieves ~92% rule-application rate when under 200 lines.

**Built-in memory hierarchy:**
```
~/.claude/CLAUDE.md          ← global (all projects)
{project-root}/CLAUDE.md     ← project (team-shared, git-tracked)
{project-root}/CLAUDE.local.md ← personal overrides (gitignored)
{subdirectory}/CLAUDE.md     ← directory-specific context
```

**Auto Memory**: Claude writes its own notes from corrections and preferences — architecture decisions, build commands, code style, debugging insights. Structured with types: `user`, `feedback`, `project`, `reference`.

**Memory plugins for Claude Code:**

| Plugin | Stars | Description | Install |
|---|---|---|---|
| [claude-mem](https://github.com/thedotmack/claude-mem) | ~41k | Auto-captures all sessions via observer AI; semantic search; 5 lifecycle hooks; SQLite | `claude mcp add claude-mem` |
| [OMEGA](https://github.com/omega-memory/omega-memory) | growing | 25 MCP tools; bge-small embeddings + sqlite-vec; auto-capture + auto-surface; daemon UDS socket | `omega setup` |
| [claude-brain](https://github.com/memvid/claude-brain) | ~174 | "Photographic memory" in a single portable `.mv2` file; Rust core; sub-ms ops; git-committable | MCP |
| [claude-diary](https://github.com/rlancemartin/claude-diary) | growing | `/diary` auto-writes learnings to `CLAUDE.md`; detects patterns (2+ = pattern, 3+ = strong); hooks into `PreCompact` | Hook-based |
| [claude_memory](https://github.com/codenamev/claude_memory) | 8 | SQLite + FTS5 + sqlite-vec; fact extraction + truth maintenance; SessionStart/Stop hooks | MCP |
| [mcp-memory-keeper](https://github.com/mkreyman/mcp-memory-keeper) | growing | Persistent context across sessions; preserves work history and decisions | MCP |
| [claude-memory-mcp](https://github.com/WhenMoon-afk/claude-memory-mcp) | growing | TypeScript + SQLite + FTS5; minimal deps; optimal LLM memory techniques | MCP |
| [my-claude-code-setup](https://github.com/centminmod/my-claude-code-setup) | ~1.8k | Starter with `CLAUDE-*.md` memory bank; `/init` populates from codebase | CLAUDE.md |
| [mem0 MCP](https://github.com/mem0ai/mem0-mcp) | growing | mem0 universal memory + OpenMemory local-first UI | `claude mcp add mem0` |
| [Graphiti MCP](https://github.com/getzep/graphiti) | ~24k | Temporal knowledge graph | Docker + config |
| [memorix](https://github.com/AVIDS2/memorix) | 144 | Cross-IDE (10 tools): git memory + reasoning memory; 22 tools | MCP |
| [Official MCP Memory](https://github.com/modelcontextprotocol/servers/tree/main/src/memory) | — | Reference knowledge graph impl; JSON file backend | MCP |

**Awesome lists:**
- [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) — skills, hooks, slash-commands, plugins

---

### OpenCode

[![GitHub Stars](https://img.shields.io/github/stars/sst/opencode?style=flat-square)](https://github.com/sst/opencode)

> Open-source terminal AI coding agent by SST. Model-agnostic, extensible plugin system, full MCP support. Sessions saved automatically; `/sessions` to switch.

- **GitHub**: https://github.com/sst/opencode
- **Instructions file**: `AGENTS.md` (same as OpenAI Codex, analogous to `CLAUDE.md`)
- **MCP**: Full support — all MCP memory servers work

**Memory plugins for OpenCode:**

| Plugin | Description |
|---|---|
| [opencode-supermemory](https://github.com/supermemoryai/opencode-supermemory) | Supermemory plugin; `/supermemory-init` to memorize codebase conventions; configurable similarity threshold |
| [opencode-mem](https://github.com/tickernelz/opencode-mem) | Local vector DB (SQLite); project memories + user profile learning; multi-provider AI |
| [opencode-agent-memory](https://github.com/joshuadavidthomas/opencode-agent-memory) | Letta/MemGPT-inspired; scoped memory blocks with size limits; agent actively maintains own memory |
| [opencode-brain](https://github.com/deiviuds/opencode-brain) | Port of claude-brain; single `.mv2` portable file; shares memory with Claude Code |
| [opencode-plugin-simple-memory](https://github.com/cnicolov/opencode-plugin-simple-memory) | Lightweight; memories stored as daily logfmt files in `.opencode/memory/` |

**Awesome list:** [awesome-opencode/awesome-opencode](https://github.com/awesome-opencode/awesome-opencode)

---

### OpenAI Codex CLI + Agents SDK

[![GitHub Stars](https://img.shields.io/github/stars/openai/codex?style=flat-square)](https://github.com/openai/codex)

> OpenAI's terminal coding agent. Multi-model support with approval workflows. Cross-session memory via the Agents SDK sessions system.

**AGENTS.md** (Codex's built-in context file):
```
Discovery order per session:
~/.codex/AGENTS.override.md → ~/.codex/AGENTS.md → {project}/AGENTS.override.md → {project}/AGENTS.md
```

**OpenAI Agents SDK Sessions** — persistent memory backends:
```python
from agents import Agent
from agents.sessions import SQLiteSession  # or RedisSession, SQLAlchemySession

agent = Agent(name="coder", instructions="Coding assistant with memory")
session = SQLiteSession("conversations.db")

# Memory persists across .run() calls
result1 = await Runner.run(agent, "My project uses FastAPI", session=session)
result2 = await Runner.run(agent, "What framework should I use?", session=session)
# Returns: "FastAPI, based on your project setup"
```

**Session backends**: SQLite (file-based), async SQLite, Redis, SQLAlchemy (Postgres/MySQL), Dapr state store, OpenAI-hosted

- **GitHub (Codex)**: https://github.com/openai/codex
- **GitHub (Agents SDK)**: https://github.com/openai/openai-agents-python
- **Docs**: https://openai.github.io/openai-agents-python/sessions/

---

### Google Gemini CLI + ADK

[![GitHub Stars](https://img.shields.io/github/stars/google-gemini/gemini-cli?style=flat-square)](https://github.com/google-gemini/gemini-cli)

> Google's open-source terminal AI agent. 1M token context window. Full MCP support. The ADK provides production-grade memory backends.

- **GitHub (CLI)**: https://github.com/google-gemini/gemini-cli
- **GitHub (ADK)**: https://github.com/google/adk-python
- **Instructions file**: `GEMINI.md` (project-level, analogous to `CLAUDE.md`)
- **MCP**: Full support — all MCP memory servers compatible

**Google ADK Memory Services:**

```python
from google.adk.agents import Agent
from google.adk.memory import InMemoryMemoryService, VertexAIMemoryBankService

# Prototyping: in-memory, keyword matching
agent = Agent(name="dev_agent", memory_service=InMemoryMemoryService())

# Production: cross-session persistence via Vertex AI
agent = Agent(
    name="dev_agent",
    memory_service=VertexAIMemoryBankService(project="my-project", location="us-central1")
)
```

**Conductor (Context-Driven Development extension):**

> Shifts development context from transient chats into persistent Markdown files stored in the repository. Defines product goals, architectural constraints, technology choices. Strict lifecycle: Context → Spec → Plan → Implement.

- **GitHub**: https://github.com/gemini-cli-extensions/conductor
- **Stars**: ~3,307
- **Install**: `gemini extensions install https://github.com/gemini-cli-extensions/conductor --auto-update`

**Gemini Code Assist Memory** (enterprise + consumer):
- Persistent memory for coding standards, style, best practices
- Enabled from Google Cloud Console (enterprise) or Gemini Code Assist site
- Uses 1M+ token context window

---

### Kimi (Moonshot AI)

[![GitHub Stars](https://img.shields.io/github/stars/MoonshotAI/kimi-cli?style=flat-square)](https://github.com/MoonshotAI/kimi-cli)

> Chinese frontier model with 256K context and native agent cluster support. The Kimi K2.5 model supports up to 100 parallel agents with shared memory storage/retrieval tools.

- **GitHub (CLI)**: https://github.com/MoonshotAI/kimi-cli — **6,400+ stars**, Apache-2.0
- **Context**: 256K tokens; sessions auto-saved; `/sessions` to view/switch
- **MCP**: Full support — `kimi mcp add/list/remove/auth`
- **API**: OpenAI-compatible (mem0, Graphiti work directly)
- **Platform**: https://platform.moonshot.ai (agent support, memory storage/retrieval tools)

**kimi-code-mcp** — delegates bulk codebase analysis to Kimi K2.5 (saving ~90% tokens), with session caching and parallel agents:
- **GitHub**: https://github.com/howardpen9/kimi-code-mcp

---

### Cursor

> AI code editor with full MCP support. Memory via `.cursor/rules` files and any MCP memory server.

- **Native memory**: `.cursor/rules` + `.cursorrules` (project and global) — persistent instructions
- **MCP config**: `.cursor/mcp.json`
- **MCP directory**: https://cursor.directory/plugins
- **Puliczek/mcp-memory**: https://github.com/Puliczek/mcp-memory — remembers user preferences and behaviors across conversations; works with Cursor, Claude, Windsurf

All MCP memory servers in this list work with Cursor.

---

### Windsurf (Codeium)

> AI-powered IDE with Cascade agentic workflows. Has two complementary memory systems: auto-generated Memories and manual Rules.

- **Cascade Memories** (automatic): Auto-generated per interaction; stored in `~/.codeium/windsurf/memories/`; workspace-scoped; retrieved when relevant; NOT committed to repo
- **Rules** (manual): Globally or workspace-defined standards; version-controlled and shareable
- **MCP**: Full support — all MCP memory servers compatible
- **cascade-memory-bank**: https://github.com/GreatScottyMac/cascade-memory-bank — Intelligent project memory for Windsurf; maintains context, documents decisions, architectural evolution
- **Docs**: https://docs.windsurf.com/windsurf/cascade/memories

---

### Aider

[![GitHub Stars](https://img.shields.io/github/stars/Aider-AI/aider?style=flat-square)](https://github.com/Aider-AI/aider)

> AI pair programming in the terminal. Session-stateless but powerful repo-map feature provides structural working memory.

- **GitHub**: https://github.com/Aider-AI/aider
- **Repo map**: Automatically builds a compact structural map of the entire codebase — acts as working memory within a session
- **CONVENTIONS.md**: Point Aider to a conventions file for static persistent instructions
- **MCP**: Supported; community uses memory-bank-mcp as cross-session workaround
- **Docs**: https://aider.chat/docs/usage/conventions.html

---

### Continue.dev

[![GitHub Stars](https://img.shields.io/github/stars/continuedev/continue?style=flat-square)](https://github.com/continuedev/continue)

> Open-source AI code assistant for VS Code and JetBrains with full MCP support.

- **GitHub**: https://github.com/continuedev/continue
- **MCP**: Full support via `config.yaml`
- **rules-memory** (Continue Hub): https://hub.continue.dev/continuedev/rules-memory — guides agent to persist/access data between sessions using `mcp/memory`
- **One-click Docker memory block**: Published by Continue + Docker on Continue Hub

```yaml
# config.yaml
mcpServers:
  - name: memory
    command: docker
    args: ["run", "-i", "--rm", "mcp/memory"]
```

---

### Cline

> VS Code AI coding assistant with full MCP support and the originator of the Memory Bank pattern.

- **Memory Bank pattern**: Structured `memory-bank/` directory with specialized markdown files tracking project goals, architecture, progress, patterns
- **cline-mcp-memory-bank**: https://github.com/dazeb/cline-mcp-memory-bank — memory system tracking progress between conversations
- **memory-bank-mcp** (remote): https://github.com/alioshr/memory-bank-mcp — works with Cursor, Cline, Claude Code
- **MCP**: Full support

---

### memorix — Cross-IDE Memory Layer

[![GitHub Stars](https://img.shields.io/github/stars/AVIDS2/memorix?style=flat-square)](https://github.com/AVIDS2/memorix)

> **Works with 10 IDEs simultaneously**: Cursor, Claude Code, OpenAI Codex, Windsurf, Gemini CLI, GitHub Copilot, Kiro, OpenCode, Antigravity, Trae. Git Memory (commits → searchable engineering memory) + Reasoning Memory (stores *why* decisions were made). 22 MCP tools. Local-first, no API keys.

- **GitHub**: https://github.com/AVIDS2/memorix

---

## 🗃️ Vector Databases

The storage layer for semantic memory — where embeddings live.

### Pinecone

> Managed/serverless vector database. Sub-10ms latency at scale. Built-in embeddings (OpenAI, Cohere, E5), rerankers. **MCP Agent with list_indexes, upsert, query tools.** $130M+ raised.

- **GitHub**: https://github.com/pinecone-io
- **MCP**: ✅ Official Pinecone MCP server

---

### Qdrant

[![GitHub Stars](https://img.shields.io/github/stars/qdrant/qdrant?style=flat-square)](https://github.com/qdrant/qdrant)

> **Rust-based.** Sophisticated filtering + vector similarity. Best free tier (1GB forever). HNSW indexing. 35+ new integrations in 2025.

- **GitHub**: https://github.com/qdrant/qdrant
- **Stars**: ~27k

---

### Milvus

[![GitHub Stars](https://img.shields.io/github/stars/milvus-io/milvus?style=flat-square)](https://github.com/milvus-io/milvus)

> Cloud-native vector DB for **massive scale**. GPU acceleration, distributed querying. Sub-50ms retrieval on billions of vectors. Used by NVIDIA, Salesforce, eBay.

- **GitHub**: https://github.com/milvus-io/milvus
- **Stars**: ~40k

---

### Weaviate

[![GitHub Stars](https://img.shields.io/github/stars/weaviate/weaviate?style=flat-square)](https://github.com/weaviate/weaviate)

> Open-source vector DB with hybrid search + GraphQL. **Agent Skills collection for Claude Code, Cursor, Copilot.**

- **GitHub**: https://github.com/weaviate/weaviate
- **Awesome**: https://github.com/weaviate/awesome-weaviate

---

### Chroma

[![GitHub Stars](https://img.shields.io/github/stars/chroma-core/chroma?style=flat-square)](https://github.com/chroma-core/chroma)

> Best for prototyping and small/medium apps. Excellent Python-first API. Default in many agent frameworks (CrewAI, A-MEM).

- **GitHub**: https://github.com/chroma-core/chroma

---

### FAISS

[![GitHub Stars](https://img.shields.io/github/stars/facebookresearch/faiss?style=flat-square)](https://github.com/facebookresearch/faiss)

> Facebook AI's library for efficient similarity search. C++ core with Python + GPU bindings. Indexed 1.5T vectors internally at Meta.

- **GitHub**: https://github.com/facebookresearch/faiss
- **Stars**: ~33k

---

### pgvector

[![GitHub Stars](https://img.shields.io/github/stars/pgvector/pgvector?style=flat-square)](https://github.com/pgvector/pgvector)

> Open-source vector similarity search **for Postgres**. HNSW indexing. Native SQL queries over vectors. Foundation for LangGraph production stacks.

- **GitHub**: https://github.com/pgvector/pgvector

---

### pgvectorscale

> Postgres extension complementing pgvector with **DiskANN** for improved performance at scale.

- **GitHub**: https://github.com/timescale/pgvectorscale

---

## 🕸️ Knowledge Graphs

Structured memory with explicit relationships between entities — ideal for temporal and multi-hop reasoning.

### Neo4j Agent Memory

> Graph-native memory with three types: short-term (conversation), long-term (entity knowledge graph), reasoning (decision traces with provenance).

- **GitHub**: https://github.com/neo4j-labs/agent-memory
- **Create Context Graph**: https://github.com/neo4j-labs/create-context-graph

---

### FalkorDB

> Direct successor to RedisGraph. Claims **496x faster P99 latency** and 6x better memory efficiency vs Neo4j. Native Graphiti backend.

- **GitHub**: https://github.com/FalkorDB/graphiti
- **Website**: https://www.falkordb.com

---

### Memgraph

[![GitHub Stars](https://img.shields.io/github/stars/memgraph/memgraph?style=flat-square)](https://github.com/memgraph/memgraph)

> Open-source **in-memory** graph database. Neo4j-compatible. Built for real-time streaming (Kafka, SQL, CSV). Up to 120x faster than Neo4j.

- **GitHub**: https://github.com/memgraph/memgraph
- **AI Toolkit**: https://github.com/memgraph/ai-toolkit (LangChain, MCP, agent integrations)

---

### Kuzu

> Embedded property graph DB. Vector + full-text search built in. Cypher. Multiple AI agent memory integrations. In-process, sub-3ms recall.

- **GitHub**: https://github.com/kuzudb/kuzu

---

## 📚 RAG Frameworks

Retrieval-Augmented Generation — the backbone of long-term knowledge memory.

### LlamaIndex

[![GitHub Stars](https://img.shields.io/github/stars/run-llama/llama_index?style=flat-square)](https://github.com/run-llama/llama_index)

> Leading document agent platform. Agentic RAG architecture. State, memory, human-in-the-loop review, reflection. Workflows for multi-step pipelines.

- **GitHub**: https://github.com/run-llama/llama_index
- **Stars**: ~45k

---

### RAGFlow

[![GitHub Stars](https://img.shields.io/github/stars/infiniflow/ragflow?style=flat-square)](https://github.com/infiniflow/ragflow)

> Enterprise knowledge base RAG with deep document understanding. Multi-source data analysis. Foundation for production RAG memory systems.

- **GitHub**: https://github.com/infiniflow/ragflow
- **Stars**: ~70k

---

### Langflow

[![GitHub Stars](https://img.shields.io/github/stars/langflow-ai/langflow?style=flat-square)](https://github.com/langflow-ai/langflow)

> Low-code builder for RAG and agentic workflows. Visual pipeline orchestration. 130k+ stars.

- **GitHub**: https://github.com/langflow-ai/langflow

---

## 🏭 Production / Session Storage

For production agents that need fast, reliable memory at scale.

### Motorhead

> Memory and information retrieval server for LLMs backed by Redis. Configurable `MAX_WINDOW_SIZE`, auto-summarization when context limit exceeded.

- **GitHub**: https://github.com/getmetal/motorhead

---

### Redis Agent Memory Server

> Fast and flexible memory using Redis. Working memory with auto-TTL, long-term promotion, background compaction.

- **GitHub**: https://github.com/redis/agent-memory-server

---

### Graphlit

> Cloud-native context layer. REST API for durable memory with citations. Real-time sync across Slack, GitHub, Jira.

- **GitHub**: https://github.com/graphlit

---

## 🏭 Industry Verticals

Memory requirements differ dramatically by domain. This section covers how agentic memory is applied across industries, including domain-specific tools, platforms, and research.

---

### Chip Design & Semiconductors

> **Memory challenge**: EDA workflows span 30+ years of proprietary tapeout data, months-long design cycles, and enormous cross-run learning from simulation sweeps. Agents must encode PPA (performance-power-area) results, tool-aware script memory (Verilog, SystemVerilog, Tcl), and design intent across the full RTL→GDS flow. All three EDA majors (Cadence, Synopsys, Siemens) are now in active agentic AI deployment — not research — as confirmed at DAC 2025.

| Tool / Resource | Stars | Description |
|---|---|---|
| [ChipNeMo (NVIDIA)](https://research.nvidia.com/publication/2023-10_chipnemo-domain-adapted-llms-chip-design) | — | 13B-param domain-adapted LLM trained on 30yr of NVIDIA design docs + Verilog + Tcl; matches LLaMA2-70B on chip tasks at 1/5th the size |
| [VerilogCoder (NVIDIA Labs)](https://github.com/NVlabs/VerilogCoder) | growing | Graph-based planning + AST waveform tracing; **94.2% on VerilogEval-Human v2** |
| [RTL-Coder (HKUST)](https://github.com/hkust-zhiyao/RTL-Coder) | growing | Open-source; outperforms GPT-3.5 on VerilogEval; HKUST |
| [OpenROAD](https://github.com/The-OpenROAD-Project/OpenROAD) | ~2.4k | Open-source RTL-to-GDS flow; foundation for LLM agents with design memory |
| [Cadence Cerebrus AI Studio](https://www.cadence.com/en_US/home/tools/digital-design-and-signoff/soc-implementation-and-signoff/cadence-cerebrus-ai-studio.html) | — | First multi-block, multi-user AI chip design; AI agents build cross-project PPA models; 5–10x faster delivery |
| [Cadence ChipStack AI Super Agent](https://www.cadence.com/en_US/home/company/newsroom/press-releases/pr/2026/cadence-unleashes-chipstack-ai-super-agent-pioneering-a-new.html) | — | Acquired Nov 2025; integrates Cerebrus + Verisium + JedAI data platform; used in 1,000+ tapeouts |
| [Cadence JedAI](https://www.cadence.com) | — | Centralized data lake feeding all Cadence AI agents with cross-run memory |
| [Cadence Verisium](https://www.cadence.com) | — | Big-data + AI across multiple simulation runs; root-cause analysis agent |
| [Synopsys AgentEngineer](https://www.synopsys.com/glossary/what-is-eda-agentic-ai.html) | — | Prototype at DAC 2025; built on Microsoft Discovery; L2→L5 autonomy roadmap; formal assertion generation |
| [Siemens Fuse EDA AI Agent](https://www.prnewswire.com/news-releases/siemens-launches-fuse-eda-ai-agent-for-automation-across-semiconductor-3d-ic-and-pcb-system-workflows-302714880.html) | — | Multi-domain agent across semiconductor, 3D IC, PCB; NVIDIA NIM + Nemotron models |
| [Siemens Questa One Agentic Toolkit](https://news.siemens.com/en-us/questa-one-agentic-ai-toolkit/) | — | Domain-scoped agents for RTL sign-off; multi-agent verification planning |
| [Awesome-LLM4EDA](https://github.com/Thinklab-SJTU/Awesome-LLM4EDA) | growing | Curated research hub for LLMs in EDA (SJTU) |
| [Chip-Design-LLM-Zoo](https://iprc-dip.github.io/Chip-Design-LLM-Zoo/) | — | Community hub of LLMs targeting chip design |
| [EDAAgent](https://arxiv.org/abs/2404.09531) | — | Autonomous EDA agent with tool-use memory for multi-step chip design tasks |

**Memory types used**: Procedural (EDA scripts, Tcl, design rules), semantic (component/IP libraries), episodic (prior tapeout PPA runs), cross-run RL (Cadence Cerebrus learning across designs)

---

### Pharmaceutical & Drug Discovery

> **Memory challenge**: Wet lab runs cost $10k–$1M+ and are irreversible. Agents must retain structure-activity relationships (SAR) across thousands of assay runs, track hypothesis lineage, and distinguish informative negatives from successes. Memory must span years-long research timelines with privacy constraints around patient trial data.

| Tool / Resource | Stars | Description |
|---|---|---|
| [ChemCrow](https://github.com/ur-whitelab/chemcrow-public) | ~1.3k | 18 expert chemistry tools + GPT-4 + LangChain; autonomously synthesized DEET; *Nature Machine Intelligence* 2024 |
| [ChemAgent](https://github.com/gersteinlab/ChemAgent) | growing | **ICLR 2025**: self-updating Planning Memory + Execution Memory + Knowledge Memory; **+46% on SciBench** vs GPT-4 baseline |
| [DrugAgent](https://github.com/FermiQ/drugagent) | growing | Multi-agent: LLM Planner + LLM Instructor; biomedical data retrieval, molecular generation, property prediction, 3D protein-ligand generation |
| [BioAgents](https://github.com/bio-xyz/BioAgents) | growing | Multi-agent: literature analysis + data scientist agents; iterative scientific discovery loop |
| [AlphaFold 3](https://github.com/google-deepmind/alphafold3) | ~15k | Structure prediction; agents use predicted structures as episodic memory priors |
| [ProteinGym](https://github.com/OATML-Markslab/ProteinGym) | ~700 | ~2.7M missense variants across 217 DMS assays; standard benchmark for mutation effect predictors |
| [Recursion OS](https://www.recursion.com/platform) | — | Automated high-throughput phenomic imaging + DL; 50B+ images; merged with Exscientia (2024); 18-month target-to-IND vs 42mo industry avg |
| [Chemistry42 (Insilico Medicine)](https://insilico.com) | — | Generative AI + DL + RL for autonomous molecular design; IPF drug candidate in Phase II clinical trials |
| [Schrödinger FEP+](https://www.schrodinger.com/products/fep) | — | Physics-based molecular simulation + ML; zasocitinib (TAK-279) advanced to Phase III |
| [AstraZeneca ChatInvent](https://www.astrazeneca.com) | — | Multi-agent architecture with GUI; evolved from single-agent proof-of-concept; integrated into discovery pipeline |
| [Awesome-BioAgent-Papers](https://github.com/aristoteleo/awesome-bioagent-papers) | growing | Curated list of LLM agent papers in biology/medicine |
| [Awesome-LLM-Agents-Scientific-Discovery](https://github.com/zhoujieli/Awesome-LLM-Agents-Scientific-Discovery) | growing | LLM agents in biomedical research, genomics, medical imaging |

**Memory types used**: Semantic (molecular property knowledge), episodic (past synthesis/assay runs), procedural (synthesis route protocols), associative (SAR relationship graphs)

**Key papers**: [AI Agents in Drug Discovery](https://arxiv.org/abs/2510.27130) (2025 survey) · [ChemAgent ICLR 2025](https://arxiv.org/abs/2501.06590) · [Democratising drug discovery through agentic AI](https://www.sciencedirect.com/science/article/pii/S1359644626000103)

---

### Healthcare & Clinical AI

> **Memory challenge**: HIPAA/GDPR mandate data minimization, consent management, role-based access, and audit trails on every memory read/write. Patient memory must span decades of EHR data with temporal coherence (drug A prescribed before condition B). Memory must distinguish verified clinical facts from clinician observations. Memory frameworks like mem0/Letta require custom compliance wrappers for healthcare production deployment.

| Tool / Resource | Description |
|---|---|
| [Epic EHR + Azure OpenAI](https://spsoft.com/tech-insights/epic-ehr-ai-trends-in-2025-reshaping-care/) | HIPAA-compliant generative AI via Microsoft Azure OpenAI; integrates longitudinal patient context into clinical workflows; deployed across 350M+ patient records |
| [Stanford HAI Longitudinal EHR](https://hai.stanford.edu/news/advancing-responsible-healthcare-ai-longitudinal-ehr-datasets) | Research initiative for training AI on long-term health patterns (chronic disease, cancer treatment) |
| [NYUTron](https://www.nature.com/articles/s41586-023-06160-y) | Hospital LLM trained on EHR data; longitudinal patient memory (*Nature* 2023) |
| [Intuitive Surgical Case Insights (da Vinci 5)](https://www.intuitive.com) | Post-surgical AI: tracks operative time per step, movement smoothness; longitudinal surgical performance profile; 25% reduction in operative time |
| [NVIDIA Autonomous Surgery Research](https://developer.nvidia.com/blog/new-ai-research-foreshadows-autonomous-robotic-surgery/) | VLM trained on surgical video + da Vinci integration; zero-shot surgical task execution via imitation learning (Johns Hopkins / Stanford) |
| [Microsoft Azure Health Data Services](https://azure.microsoft.com/en-us/products/health-data-services) | HIPAA-compliant memory store for clinical AI agents |
| [AWS HealthLake](https://aws.amazon.com/healthlake/) | FHIR-native memory for clinical agents with semantic search |
| [Ambience Healthcare](https://www.ambiencehealthcare.com) | AI ambient documentation — episodic memory of clinical encounters |
| [Abridge](https://www.abridge.com) | AI for clinical notes with session memory and longitudinal context |
| [PathAI](https://www.pathai.com) | Pathology AI with memory of prior case patterns for diagnostic agents |

**Memory types used**: Longitudinal episodic (encounter history across decades), semantic (ICD-10, SNOMED, drug interactions), temporal (lab value trends, disease progression), working memory (current encounter context)

**Key papers**: [Comprehensive Survey of AI Agents in Healthcare](https://www.nztang.com/assets/files/papers/xu_techrxiv25.pdf) · [Foundational Architecture for AI Agents in Healthcare](https://pmc.ncbi.nlm.nih.gov/articles/PMC12629813/)

---

### Finance & Trading

> **Memory challenge**: Markets are adversarial — memory of past regimes can mislead if conditions change. Agents must distinguish regime memory (bull/bear) from event memory (earnings) from behavioral memory (client risk tolerance). Fraud detection requires continuously updating behavioral baselines without concept drift. MiFID II and SEC require auditable memory access logs.

| Tool / Resource | Stars | Description |
|---|---|---|
| [FinMem](https://github.com/pipiku915/FinMem-LLM-StockTrading) | growing | **Layered memory** (short/medium/long-term cognitive spans) mirroring human trader cognition; ICLR Workshop + IEEE 2025 |
| [FinAgent](https://github.com/AI4Finance-Foundation/FinAgent) | growing | Multimodal foundation agent; layered memorization + technical indicators; **KDD 2024** |
| [HedgeAgents](https://arxiv.org/pdf/2412.20138) | — | Balance-aware multi-agent financial trading; 2025 |
| [FinGPT](https://github.com/AI4Finance-Foundation/FinGPT) | ~15k | Open-source financial LLM with news and market data memory |
| [TradingGPT](https://github.com/stevehuang52/TradingGPT) | growing | GPT-based trading agent with multi-layer memory and diverse roles |
| [AI4Finance-Foundation](https://github.com/AI4Finance-Foundation) | — | Org with 15+ financial agent + memory repos |
| [OpenBB](https://github.com/OpenBB-finance/OpenBB) | ~35k | Open-source financial terminal — foundation for agents with financial data memory |
| [Sardine](https://www.sardine.ai) | — | Behavioral biometrics + transaction graph memory for real-time fraud, credit, compliance |
| [IBM AI Fraud Detection](https://www.ibm.com/think/topics/ai-fraud-detection-in-banking) | — | Behavioral signature memory: keystroke cadence, mouse trajectories, touchscreen pressure |
| [Visa Agentic AI](https://www.visaacceptance.com/en-us/blog/article/2025/agentic-ai-fraud-impact.html) | — | Real-time transaction fraud; behavioral memory across millions of accounts |
| [Bloomberg GPT](https://arxiv.org/abs/2303.17564) | — | Finance domain LLM; agents use semantic memory over Bloomberg terminal data |

**Memory types used**: Layered temporal (short/medium/long-term price memory), episodic (trade outcomes), semantic (financial knowledge), behavioral biometrics (fraud), client preference (wealth management)

**Key papers**: [FinMem: Performance-Enhanced LLM Trading Agent](https://arxiv.org/abs/2311.13743) · [FinAgent: Multimodal Foundation Agent](https://arxiv.org/html/2402.18485v3)

---

### Legal & Compliance

> **Memory challenge**: Every retrieved memory must link back to authoritative source (case, statute, regulation) — hallucinated precedents have caused real attorneys to be sanctioned. Memory must handle temporal validity (an overruled precedent is dead memory). Jurisdiction-scoping is critical. One 2024 study found specialized legal LLMs hallucinate 17–33% of the time even when marketed as "hallucination-free."

| Tool / Resource | Stars | Description |
|---|---|---|
| [Harvey AI](https://harvey.ai) | — | **700+ clients, 42% of AmLaw 100**; "Vault" knowledge base for firm-specific memory; $8B valuation (Oct 2025); LexisNexis partnership June 2025 |
| [Thomson Reuters CoCounsel](https://thomsonreuters.com) | — | Acquired from Casetext ($650M); semantic search over TR's authoritative legal database |
| [LexisNexis Lexis+ AI](https://www.lexisnexis.com) | — | Legal research with semantic memory over 4M+ case documents |
| [OLAW (Harvard LIL)](https://github.com/harvard-lil/olaw) | growing | Open Legal AI Workbench; RAG for legal AI research; CourtListener API; Harvard Library Innovation Lab |
| [LegalBench](https://github.com/HazyResearch/legalbench) | ~800 | 162 legal reasoning tasks; agents need procedural + semantic memory |
| [LLM-and-Law](https://github.com/Jeryi-Sun/LLM-and-Law) | growing | Papers: LawBench, LegalAgentBench, and more |
| [LawAgent](https://github.com/AI-Hub-Admin/LawAgent) | growing | Curated list of law and legal AI agent resources |
| [GC.ai](https://gc.ai) | — | AI platform for in-house legal teams with document memory |
| [EvenUp](https://www.evenuplaw.com) | — | Demand letter automation with memory of case facts and medical records |
| [Ironclad AI](https://ironcladapp.com) | — | Contract management with clause memory and negotiation history |
| [Relativity aiR](https://www.relativity.com) | — | eDiscovery with document memory for review agents |

**Memory types used**: Semantic (statute/case databases), episodic (matter history), temporal (precedent validity windows — knowing when a case was overruled), procedural (jurisdiction-specific playbooks)

---

### Manufacturing & Industrial IoT

> **Memory challenge**: OT (operational technology) networks are often air-gapped from IT — cloud-based memory is unavailable on the factory floor. Local/edge memory is mandatory. Safety-critical environments mean a wrong action from stale memory can cause injury or catastrophic failure. Multi-shift operations require temporal memory handoffs across crews. Gartner named agentic AI the #1 technology trend for 2025; Deloitte projects 50% of GenAI enterprises will deploy autonomous industrial agents by 2027.

| Tool / Resource | Description |
|---|---|
| [XMPro APEX](https://xmpro.com/agentic-ai/agentic-platform-experience/) | Policy-constrained execution; shared memory across agent teams; coordinates specialized agents with structured memory and planning frameworks |
| [XMPro MAGS](https://xmpro.com/agentic-ai/multi-agent-generative-systems/) | Multi-Agent Generative Systems; self-organizing teams; real-time industrial awareness; **250%+ documented ROI; $10M/yr savings** at potash mining customer |
| [NVIDIA Omniverse + Isaac](https://developer.nvidia.com/omniverse) | Simulation platform for manufacturing agents with persistent environment memory |
| [PTC ThingWorx + AI](https://www.ptc.com/en/products/thingworx) | Industrial IoT platform with time-series memory for production agents |
| [OSIsoft PI (AVEVA)](https://www.aveva.com/en/products/aveva-pi-system/) | Historian-based memory for industrial process agents |
| [Rockwell Automation FactoryTalk AI](https://www.rockwellautomation.com) | Factory operations agent with production history memory |
| [Siemens Industrial Copilot](https://www.siemens.com/global/en/products/automation/industry-software/industrial-ai.html) | Generative AI for automation with persistent machine context |
| [GE Predix (Vernova)](https://www.ge.com/digital/applications/asset-performance-management) | Asset performance management with long-term equipment memory |

**Memory types used**: Temporal (sensor time-series, equipment lifecycle), episodic (failure events, maintenance records), semantic (equipment specs, failure modes), procedural (SOPs)

---

### Scientific Research & Labs

> **Memory challenge**: Scientific memory must support causal chains spanning months or years. Reproducibility mandates that the exact memory state at the time of discovery be recoverable. Self-driving labs need memory bridging robotic hardware state, experimental parameters, and statistical models simultaneously. Key research finding: "Current memory architectures are ill-equipped to store, retrieve, and reason across diverse data types seamlessly." — Agentic Science Survey 2025

| Tool / Resource | Stars | Description |
|---|---|---|
| [AgentLaboratory](https://github.com/SamuelSchmidgall/AgentLaboratory) | growing | End-to-end autonomous research: literature review → experiment → report; arXiv 2501.04227; **84% cost reduction** vs prior methods |
| [AgentRxiv](https://agentrxiv.github.io) | — | Agents upload, retrieve, and build on each other's research; shared cumulative memory; improved MATH-500 from 70.2% → 79.8% via collaboration |
| [Awesome-Self-Driving-Labs](https://github.com/AccelerationConsortium/awesome-self-driving-labs) | growing | Community-curated: hardware automation + AI closed-loop lab workflows |
| [Awesome-AI-for-Science](https://github.com/ai-boost/awesome-ai-for-science) | growing | Physics, chemistry, biology, materials — multi-domain science agent resources |
| [ChemCrow](https://github.com/ur-whitelab/chemcrow-public) | ~1.3k | Chemistry lab agent with memory of reactions, reagents, synthesis routes |
| [Emerald Cloud Lab](https://www.emeraldcloudlab.com) | — | Fully automated research lab with programmable experiment memory |
| [Benchling](https://www.benchling.com) | — | Life science R&D platform with experiment and protocol memory |
| [MLflow](https://github.com/mlflow/mlflow) | ~20k | ML experiment tracking — episodic memory for model training agents |
| [Weights & Biases](https://wandb.ai) | — | Experiment tracking with rich run memory for AI/ML research agents |
| [Elicit](https://elicit.com) | — | AI research assistant with memory of literature and hypotheses |
| [ORNL HPC Experiment Agents](https://dl.acm.org/doi/full/10.1145/3731599.3767592) | — | AI agents for autonomous experiments at Oak Ridge National Lab (ACM SC '25) |

**Memory types used**: Episodic (experiment runs), semantic (domain literature), procedural (protocols, synthetic routes), causal (hypothesis→experiment→result chains)

**Key papers**: [Agentic AI for Scientific Discovery Survey](https://arxiv.org/html/2503.08979v1) · [AgentRxiv: Collaborative Autonomous Research](https://agentrxiv.github.io)

---

### Autonomous Vehicles & Robotics

> **Memory challenge**: Spatial memory must operate at millisecond latency. Episodic memory must support counterfactual reasoning ("what if I had turned left?"). Safety-critical applications mean memory failures can be life-threatening. Long-horizon navigation requires persistent topological maps valid across sessions, seasons, and environmental changes. Waymo's hybrid architecture pairs "fast-thinking" sensor fusion (breaks scene into objects) with "slow-thinking" VLM (holistic scene understanding) — mirroring dual-process cognitive theory.

| Tool / Resource | Stars | Description |
|---|---|---|
| [RoboMemory](https://arxiv.org/html/2508.01415) | — | Brain-inspired: Spatial + Temporal + Episodic + Semantic under parallelized architecture; lifelong learning in physical embodied systems |
| [ELLA (Embodied Lifelong Learning)](https://arxiv.org/pdf/2506.24019) | — | Name-centric semantic memory (hierarchical scene graphs + KGs) + spatiotemporal episodic memory; multi-modal experience capture |
| [Hydra (MIT SPARK)](https://github.com/MIT-SPARK/Hydra) | ~700 | 3D scene graph SLAM for spatial memory in robots; real-time hierarchical map maintenance |
| [SayPlan](https://arxiv.org/abs/2307.06135) | — | Scene graph-based semantic memory for robotic long-horizon task planning |
| [VoxPoser](https://arxiv.org/abs/2307.05973) | — | LLM + spatial value maps as robot working memory for manipulation |
| [RT-2 (Google DeepMind)](https://arxiv.org/abs/2307.15818) | — | Robotics Transformer with implicit semantic memory from internet-scale pretraining |
| [Waymo EMMA](https://waymo.com/blog/2024/10/introducing-emma/) | — | Built on Gemini; processes raw camera + text; chain-of-thought planning; **+6.7% end-to-end planning** |
| [Waymo World Model](https://waymo.com/blog/2026/02/the-waymo-world-model-a-new-frontier-for-autonomous-driving-simulation/) | — | Built on Genie 3 (Feb 2026); generative world model for hyper-realistic simulation memory |
| [Tesla FSD](https://arxiv.org/abs/2307.05346) | — | RNN ensemble predicting 5-second trajectory horizons; camera-only spatial memory |
| [Awesome-Embodied-Robotics-and-Agent](https://github.com/zchoi/Awesome-Embodied-Robotics-and-Agent) | growing | Curated LLM-powered embodied AI research |
| [Awesome-LLM4AD](https://github.com/Thinklab-SJTU/Awesome-LLM4AD) | growing | LLM/VLM/VLA/World Model for autonomous driving (SJTU) |
| [Awesome-World-Model](https://github.com/LMD0311/Awesome-World-Model) | growing | World models for autonomous driving and robotics |

**Memory types used**: Spatial (3D scene graphs, HD maps), episodic (trajectory history), procedural (motor skills), temporal (world model predictions)

**Key papers**: [RoboMemory](https://arxiv.org/abs/2508.01415) · [ELLA](https://arxiv.org/abs/2506.24019) · [Waymo EMMA](https://waymo.com/blog/2024/10/introducing-emma/)

---

### Education & Tutoring

> **Memory challenge**: Memory must track learning trajectory across months/years, preserve productive struggle history (knowing *where* a student got stuck is as valuable as knowing they got an answer wrong), and adapt to changing proficiency without catastrophic forgetting. FERPA and COPPA for minors constrain persistence. Memory serves two principals — student and teacher — with different access scopes.

| Tool / Resource | Description |
|---|---|
| [Khanmigo (Khan Academy)](https://www.khanmigo.ai) | Chat history → interest identification → personalized teaching; "Interests" memory feature (2025); hundreds of thousands of active users |
| [Carnegie Learning MATHia](https://www.carnegielearning.com/products/software-platform/math-software/) | Real-time performance analysis; adjusts difficulty/pacing; trained on **1.2B math problems from 5.5M students over 25 years** — one of the largest longitudinal behavioral memory datasets in any domain |
| [Carnegie Learning LiveHint AI](https://www.carnegielearning.com) | LLM-based math tutor for middle/high school built on the 25yr behavioral memory dataset |
| [Duolingo Max](https://blog.duolingo.com/duolingo-max) | Roleplay and explanation features with user proficiency memory |
| [Synthesis Tutor](https://www.synthesis.com) | Problem-solving tutor with student challenge history |
| [mem0 + Education](https://mem0.ai/blog/personalised-tutoring-agent-with-mem0-and-openai) | Tutorial: Personalized tutoring agent using mem0 for student memory |

**Memory types used**: Longitudinal episodic (learning history), semantic (curriculum knowledge), procedural (pedagogical strategies), behavioral (engagement and struggle patterns)

**Key paper**: [AI-Powered Educational Agents: 82-study systematic review](https://www.mdpi.com/2078-2489/16/6/469) (MDPI, Jan 2023 – Feb 2025)

---

### Space Research & Exploration

> **Memory challenge**: Space missions have ultra-high-latency communication (up to 24 minutes one-way to Mars). Autonomous agents must carry all operational memory onboard — they cannot ask ground control in real time. Every byte of memory must count.

| Tool / Resource | Description |
|---|---|
| [NASA JPL OPEN-SOURCE ROVER](https://github.com/nasa-jpl/open-source-rover) | Open platform for building rovers with programmable memory modules |
| [NASA Ames Planner/Scheduler (Europa)](https://ti.arc.nasa.gov/tech/aif/planning-and-scheduling/) | Autonomous planning with mission episodic memory — used on Curiosity and Perseverance |
| [CODEX (JPL)](https://www-robotics.jpl.nasa.gov/how-we-do-it/systems/spacecraft-autonomy/) | Onboard AI executive with persistent state memory for deep space |
| [ESA INTEGRAL Memory Agent](https://www.esa.int) | Autonomous fault detection with long-term behavioral memory |
| [AstroLLaMA](https://arxiv.org/abs/2309.06126) | Domain-adapted LLM for astronomy; agents on top use semantic memory over arXiv astro papers |
| [Astropy](https://github.com/astropy/astropy) | Core astronomy Python library — foundation for science agents with observational memory |
| [LSST/Rubin Observatory AI](https://www.lsst.org) | Vera Rubin's alert pipeline: episodic memory of 10M+ nightly transient events for autonomous follow-up agents |
| [ExoplanetArchive + RAG](https://exoplanetarchive.ipac.caltech.edu) | NASA Exoplanet Archive; research agents use it as semantic memory for planetary science |
| [OpenSpace](https://github.com/OpenSpace/OpenSpace) | Interactive data visualization of the universe — spatial memory layer for space exploration agents |
| [Space-LLaVA](https://arxiv.org/abs/2501.08983) | Multimodal space agent with satellite image memory |

**Memory types used**: Episodic (mission log, telemetry history), semantic (astronomical catalogs), procedural (fault-recovery playbooks), spatial (3D star maps and orbital mechanics)

---

### Smart Agriculture & Livestock

> **Memory challenge**: AI systems monitoring animals and crops must track individual animals over their lifetime (years), seasonal patterns, behavioral deviations, and genetic histories — at farm scale across thousands of animals.

| Tool / Resource | Description |
|---|---|
| [Connecterra Ida (Cow AI)](https://www.connecterra.io) | **The "AI cow collar"** — accelerometer + ML with per-cow episodic memory of rumination, walking, lying, eating patterns; detects illness days before symptoms show clinically |
| [CattleEye](https://cattleeye.com) | Computer vision livestock monitoring with individual animal identity memory |
| [Cainthus (acquired by Ever.Ag)](https://ever.ag) | Dairy cow facial recognition + behavior memory for 24/7 herd monitoring |
| [SmaXtec](https://www.smaxtec.com) | Bolus sensors in cattle stomachs — continuous rumination + temperature memory per animal |
| [Moocall](https://moocall.com) | Calving sensor with temporal behavioral memory to predict birth within 1 hour |
| [Halter (Smart Cattle Collars)](https://www.halter.com) | GPS + virtual fencing collar with spatial and behavioral memory per animal, NZ-based |
| [John Deere See & Spray](https://www.deere.com/en/sprayers/see-spray-ultimate/) | Precision agriculture with semantic memory of field weed maps |
| [Climate Corporation (Bayer)](https://climate.com) | Digital farming with seasonal yield memory and predictive field agents |
| [FarmBot](https://github.com/FarmBot/Farmbot-Web-App) | Open-source precision agriculture robot with crop growth memory |
| [Arable Mark](https://www.arable.com) | Field sensors with long-term microclimate and crop-stage memory for farm agents |
| [Taranis](https://www.taranis.com) | Aerial scouting AI with field-level pest and disease episodic memory |

**Memory types used**: Episodic (individual animal behavioral history), temporal (seasonal patterns), semantic (breed and disease databases), spatial (field and pasture maps)

---

### Climate Science & Environmental Monitoring

> **Memory challenge**: Climate agents operate over decades of data — extreme events, emissions trajectories, ocean temperatures, ice core records — requiring temporal memory that spans centuries.

| Tool / Resource | Description |
|---|---|
| [ClimaX](https://github.com/microsoft/ClimaX) | Microsoft's foundation model for weather and climate with temporal atmospheric memory |
| [Aurora (Microsoft)](https://arxiv.org/abs/2405.13063) | AI weather model trained on 1M+ hours of data; agents use atmospheric state as working memory |
| [GraphCast (DeepMind)](https://arxiv.org/abs/2212.12794) | 10-day weather forecasting; episodic memory of atmospheric states at 6-hour intervals |
| [Pangeo](https://pangeo.io) | Community platform for big ocean/climate data — semantic memory layer for climate agents |
| [Earth System Grid Federation](https://esgf.llnl.gov) | Archive of climate simulation outputs — long-term climate memory at petabyte scale |
| [NASA Earthdata](https://www.earthdata.nasa.gov) | Satellite + sensor archive for environmental agents — decades of episodic Earth observations |
| [ClimateGPT](https://arxiv.org/abs/2401.09646) | LLM for climate science with semantic memory over IPCC reports and scientific literature |
| [WildfireGPT](https://arxiv.org/abs/2402.07877) | Wildfire analysis agent with temporal memory of fire history and climate data |
| [Open Climate Fix](https://github.com/openclimatefix) | ML for clean energy — agents with solar irradiance and grid memory |

**Memory types used**: Temporal (climate time-series spanning decades), semantic (climate science ontologies), episodic (extreme event records), spatial (geospatial grids)

---

### Defense & Intelligence

> **Memory challenge**: Defense agents operate in adversarial environments where memory itself can be a target (adversarial poisoning, deception attacks). Memory must be auditable for chain-of-command accountability. DARPA's L2M program explicitly targets catastrophic forgetting — a robot deployed in year 1 must still perform year-1 tasks in year 3 while having learned new ones. Memory in this domain must be adversarially robust.

| Program / Tool | Description |
|---|---|
| [DARPA L2M (Lifelong Learning Machines)](https://www.darpa.mil/research/programs/lifelong-learning-machines) | Develops systems that **learn continuously during execution**, become increasingly expert, apply prior skills to new tasks without forgetting; bio-inspired memory mechanisms |
| [DARPA GARD](https://defensescoop.com/2024/03/27/darpa-transitions-tech-gard-program-cdao/) | Guaranteeing AI Robustness against Deception; addresses memory poisoning and deception attacks; transitioned to DoD CDAO |
| [DARPA REMA](https://www.darpa.mil) | Rapid Experimental Missionized Autonomy; $13.8M FY2025; autonomous operation subsystems for military drones |
| [DARPA SABER](https://www.darpa.mil/news/2025/saber-warfighter-ai) | Operational AI security exercises; evaluates AI-enabled autonomous ground and aerial systems in battlefield settings |
| [DARPA AIxCC](https://www.darpa.mil/news/2025/aixcc-results) | AI agents autonomously finding/fixing open-source CVEs; demonstrated faster-than-human performance on real vulnerabilities |
| [DARPA INSPIRE](https://viterbischool.usc.edu/news/2025/07/new-darpa-funded-project-aims-to-unravel-the-brains-learning-secrets/) | Investigates Long-Term Synaptic Plasticity (LTSP); USC-funded; translates biological memory formation into AI systems |
| [Palantir Gotham + AIP](https://www.palantir.com/platforms/aip/) | AI platform for defense with persistent entity and event memory across intelligence streams |
| [Anduril Lattice](https://www.anduril.com/product/lattice/) | Autonomous systems OS with shared battlefield memory across sensor networks |
| [Lockheed Martin (DARPA contract)](https://news.lockheedmartin.com/2024-07-08-lockheed-martin-awarded-contract-to-develop-artificial-intelligence-tools-for-darpa) | DARPA contract for AI/ML tool development; July 2024 |

**Memory types used**: Lifelong/continual (L2M program), procedural (mission playbooks), episodic (operational history), adversarially-robust semantic (GARD program)

---

### Energy & Utilities

> **Memory challenge**: Power grids operate 24/7 with decades of equipment, outage histories, and load patterns. Memory is critical for predictive maintenance, demand forecasting, and autonomous grid balancing.

| Tool / Resource | Description |
|---|---|
| [GridDynamics + AI](https://www.griddynamics.com/energy) | Grid management agents with long-term outage and demand memory |
| [Uplight](https://uplight.com) | Utility customer engagement AI with behavioral energy-use memory |
| [AutoGrid (Enel)](https://www.auto-grid.com) | Virtual power plant with distributed energy resource (DER) memory |
| [Open Climate Fix Solar](https://github.com/openclimatefix/nowcasting_dataset) | Solar irradiance forecasting agents with location-specific generation history |
| [ENERTIV](https://www.enertiv.com) | Building energy agents with HVAC behavioral and anomaly memory |
| [Sievert (Arcadia)](https://www.arcadia.com) | Energy data platform — semantic memory over utility rates and usage |

---

### Cross-Vertical Summary

| Vertical | Primary Memory Type | Key Constraint | Dominant Architecture |
|---|---|---|---|
| Chip / EDA | Procedural + cross-run RL | Decades of proprietary tapeout data | Domain-adapted LLM + KV store + cross-run learning DB |
| Pharma | SAR episodic + causal | Irreversibility + wet lab cost | KG + molecular database + hypothesis chain |
| Healthcare | Longitudinal episodic | HIPAA/GDPR compliance | HIPAA-compliant vector store + EHR-integrated retrieval |
| Finance | Layered temporal | Regime shifts + regulatory audit | Layered memory (short/medium/long-term) + behavioral biometrics |
| Legal | Semantic + temporal validity | Citation traceability + hallucination risk | RAG over authoritative corpus + precedent validity tracking |
| Manufacturing | Temporal sensor + procedural | Edge deployment (no cloud) + safety | Local time-series DB + equipment knowledge graph |
| Science / Lab | Causal chain + episodic | Reproducibility + long-horizon reasoning | KG + protocol memory + cumulative shared memory |
| AV / Robotics | Spatial + world model | Real-time latency + safety | 3D scene graph + world model + episodic trajectory buffer |
| Education | Behavioral longitudinal | FERPA/COPPA + dual-principal access | Student mastery model + longitudinal interaction history |
| Defense | Lifelong continual | Adversarial robustness + catastrophic forgetting | Bio-inspired continual learning + adversarially-robust encoding |
| Space | Episodic + onboard-only | Communication latency + memory budget | Onboard planner + mission episodic log + astronomical catalogs |
| Agriculture | Episodic per-entity | Lifetime animal/crop tracking at farm scale | Sensor time-series + spatial map + individual identity memory |
| Climate | Temporal (century-scale) | Data volume + temporal span | Petabyte climate archives + geospatial grids |
| Energy | Temporal sensor | Real-time grid balancing | Time-series DB + demand forecasting memory |

### Cross-Vertical Research Collections

- [Shichun-Liu/Agent-Memory-Paper-List](https://github.com/Shichun-Liu/Agent-Memory-Paper-List) — accompanies the "Memory in the Age of AI Agents" survey
- [TeleAI-UAGI/Awesome-Agent-Memory](https://github.com/TeleAI-UAGI/Awesome-Agent-Memory) — long-term context, retrieval, reasoning
- [Elvin-Yiming-Du/Survey_Memory_in_AI](https://github.com/Elvin-Yiming-Du/Survey_Memory_in_AI) — datasets, methods, tools across all memory research
- [tmgthb/Autonomous-Agents](https://github.com/tmgthb/Autonomous-Agents) — daily-updated autonomous agent research papers
- [AgenticScience/Awesome-Agent-Scientists](https://github.com/AgenticScience/Awesome-Agent-Scientists) — agents for science, multi-domain
- [zchoi/Awesome-Embodied-Robotics-and-Agent](https://github.com/zchoi/Awesome-Embodied-Robotics-and-Agent) — embodied AI for robotics
- [aristoteleo/awesome-bioagent-papers](https://github.com/aristoteleo/awesome-bioagent-papers) — LLM agents in biology and medicine

---

## 📖 Research Papers

> Foundational and cutting-edge research on agent memory systems.

| Paper | Venue | Links | Key Contribution |
|---|---|---|---|
| MemGPT: Towards LLMs as Operating Systems | NeurIPS 2023 | [arXiv](https://arxiv.org/abs/2310.08560) | OS-inspired virtual context management |
| A Survey on the Memory Mechanism of LLM-based Agents | 2024 | [arXiv](https://arxiv.org/abs/2404.13501) | Systematic review of memory module design |
| LongMemEval: Benchmarking Chat Assistants on Long-Term Memory | ICLR 2025 | [arXiv](https://arxiv.org/abs/2410.10813) · [GitHub](https://github.com/xiaowu0162/LongMemEval) | 500-question evaluation benchmark |
| Memory in the Age of AI Agents: A Survey | 2024 | [arXiv](https://arxiv.org/abs/2512.13564) · [GitHub](https://github.com/Shichun-Liu/Agent-Memory-Paper-List) | Taxonomy: token-level, parametric, latent |
| Zep: Temporal Knowledge Graph Architecture | 2025 | [arXiv](https://arxiv.org/abs/2501.13956) | Temporal KG with validity windows |
| A-MEM: Agentic Memory for LLM Agents | NeurIPS 2025 | [arXiv](https://arxiv.org/abs/2502.12110) · [GitHub](https://github.com/agiresearch/A-mem) | Zettelkasten-inspired dynamic memory |
| Hindsight is 20/20 | 2025 | [arXiv](https://arxiv.org/abs/2512.12818) · [GitHub](https://github.com/vectorize-io/hindsight) | 4-network biomimetic, 91.4% LongMemEval |
| MemOS: OS for Memory-Augmented LLMs | 2025 | [arXiv](https://arxiv.org/abs/2505.22101) | OS metaphor for LLM memory management |
| MemoryAgentBench | ICLR 2026 | [GitHub](https://github.com/HUST-AI-HYZ/MemoryAgentBench) | Incremental multi-turn interaction benchmark |
| RoboMemory: Brain-inspired Memory for Robots | 2025 | [arXiv](https://arxiv.org/abs/2508.01415) | Spatial + Temporal + Episodic for physical robots |
| Ella: Embodied Social Agents with Lifelong Memory | 2025 | [arXiv](https://arxiv.org/abs/2506.24019) | Lifelong memory for social embodied agents |
| Rethinking Memory Mechanisms of Foundation Agents | 2026 | [arXiv](https://arxiv.org/abs/2602.06052) | Survey of second-generation memory trends |

---

## 📏 Benchmarks & Evaluation

| Benchmark | GitHub | Metric | Key Finding |
|---|---|---|---|
| **LongMemEval** (ICLR 2025) | [GitHub](https://github.com/xiaowu0162/LongMemEval) | 500 Q, 5 categories | GPT-4o drops 30% on long-term recall |
| **MemoryAgentBench** (ICLR 2026) | [GitHub](https://github.com/HUST-AI-HYZ/MemoryAgentBench) | Incremental multi-turn | Tests incremental fact acquisition |
| **MemBench** (ACL 2025) | ACL Anthology | Factual + reflective | Tests both storage and reasoning |
| **MemoryBench** (Supermemory) | [GitHub](https://github.com/supermemoryai/supermemory) | Cross-provider comparison | Open framework for comparing systems |
| **LongBench** | [GitHub](https://github.com/THUDM/LongBench) | Long-context tasks | General long-context evaluation |

---

## 📚 Awesome Paper Collections

- [TsinghuaC3I/Awesome-Memory-for-Agents](https://github.com/TsinghuaC3I/Awesome-Memory-for-Agents) — curated papers on agent memory
- [TeleAI-UAGI/Awesome-Agent-Memory](https://github.com/TeleAI-UAGI/Awesome-Agent-Memory) — papers + systems
- [Shichun-Liu/Agent-Memory-Paper-List](https://github.com/Shichun-Liu/Agent-Memory-Paper-List) — accompanies the 2024 survey
- [DEEP-PolyU/Awesome-GraphMemory](https://github.com/DEEP-PolyU/Awesome-GraphMemory) — graph-based memory specific
- [letta-ai/awesome-letta](https://github.com/letta-ai/awesome-letta) — Letta/MemGPT ecosystem

---

## 📖 Learning Resources

### Tutorials & Guides

- [LangMem Quick Start](https://langchain-ai.github.io/langmem/tutorials/) — Build a personal assistant with persistent memory
- [mem0 Documentation](https://docs.mem0.ai) — Complete guides for all backends
- [Letta Academy](https://letta.com/academy) — Agent stateful memory course
- [Graphiti Tutorial](https://github.com/getzep/graphiti/tree/main/examples) — Temporal KG examples
- [MCP Memory Guide](https://modelcontextprotocol.io/docs/guides/memory) — Official MCP memory documentation

### Courses & Videos

- [Building AI Agents with Memory — DeepLearning.AI](https://www.deeplearning.ai/courses/) — mem0 course
- [LangGraph Memory Deep Dive](https://www.youtube.com/watch?v=_W27nfYZJAc) — LangChain YouTube channel
- [MemGPT Paper Walkthrough](https://www.youtube.com/watch?v=nQmZmFERmrg) — Original OS-inspired memory

### Key Concepts

| Term | Definition |
|---|---|
| **Episodic Memory** | Records of past events and interactions |
| **Semantic Memory** | General facts and knowledge |
| **Procedural Memory** | How to perform tasks (skills, workflows) |
| **Working Memory** | Active context window |
| **Archival Memory** | Long-term storage requiring search |
| **Temporal KG** | Knowledge graph where facts have validity time windows |
| **RAG** | Retrieval-Augmented Generation — fetching relevant memories |
| **MCP** | Model Context Protocol — standard for memory server plugins |

---

## 🤝 Contributing

This list is built and maintained by the community. Every contribution helps.

**Adding a new entry:**

1. Fork the repo
2. Add your entry under the appropriate section
3. Follow the format: `[Name](URL) — Brief description (one line max)`
4. Ensure the project is open-source OR has free public documentation
5. The project must be actively maintained (last commit within 12 months)
6. Submit a PR with the title `Add [ProjectName] to [Section]`

**Criteria for inclusion:**
- Solves a real memory problem for AI agents
- Has working documentation or examples
- Not abandoned/archived (unless historically significant)
- No pure self-promotion — must provide value to others

**Improving existing entries:**

- Fix broken links
- Update star counts
- Add missing code examples
- Fix descriptions

See [CONTRIBUTING.md](CONTRIBUTING.md) for full guidelines.

---

## ⭐ Star History

[![Star History Chart](https://api.star-history.com/svg?repos=aviskaar/awesome-agentic-memory&type=Date)](https://star-history.com/#aviskaar/awesome-agentic-memory&Date)

---

<div align="center">

**If this list saved you time, please consider starring it ⭐**

Maintained by [@aviskaar](https://github.com/aviskaar) and [contributors](https://github.com/aviskaar/awesome-agentic-memory/graphs/contributors)

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

</div>
