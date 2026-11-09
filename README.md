# Awesome SuperAgent [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of resources, guides, and tools for DeepSeek's SuperAgent (`dsh-superagent`).

SuperAgent is an open-source research prototype from the DeepSeek Harness team, released on October 31, 2026. It is a proactive coding agent for one GitHub repository (and optionally Feishu chats). A long-running **Router** talks to people and dispatches work, and isolated **Worker** sessions do the work in parallel and answer in the original conversation, often with a pull request. It ships as a bundle for DeepSeek Harness under the MIT license.

Its guiding principle: *take as little human attention as possible, and give as much value as possible.*

> [!WARNING]
> DeepSeek labels SuperAgent a research prototype, "not an official DeepSeek product". Its Router and Workers run commands as your operating-system user with full access. Run it on an isolated machine or account, and read the Security section first.

This list is community-maintained and not affiliated with DeepSeek.

## Contents

- [Official Resources](#official-resources)
  - [Documentation](#documentation)
  - [Prompts and Skills](#prompts-and-skills)
- [DeepSeek Harness](#deepseek-harness)
- [Guides and Tutorials](#guides-and-tutorials)
- [Deep Dives and Analysis](#deep-dives-and-analysis)
- [Security](#security)
- [Tools and Extensions](#tools-and-extensions)
  - [Sources](#sources)
  - [Panels and UI](#panels-and-ui)
  - [Ports](#ports)
  - [Forks](#forks)
  - [Developer Tools](#developer-tools)
  - [Built on SuperAgent](#built-on-superagent)
- [Reimplementations](#reimplementations)
- [Related Projects](#related-projects)
- [Translations](#translations)
- [News](#news)

## Official Resources

- [dsh-superagent-prototype](https://github.com/deepseek-ai/dsh-superagent-prototype) - The official source code, a TypeScript bundle for DeepSeek Harness.
- [Exploring Super-agent Design: Towards a More Autonomous Agent System](https://x.com/DeepSeekHarness/status/2116857257245987236) - The design article, as a machine-translated English post from the DeepSeek Harness team.
- [Exploring Super-agent Design (Chinese original)](https://mp.weixin.qq.com/s/zoS7GlReWPhfCjENGxXCdg) - The original article on the team's WeChat account.
- [SETUP.md](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/SETUP.md) - Instructions for a coding agent that sets up SuperAgent with you, one question at a time.
- [Example profile patch](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/examples/profile.cordis.patch.yml) - A minimal Harness profile configuration for SuperAgent.
- [@DeepSeekHarness](https://x.com/DeepSeekHarness) - The DeepSeek Harness team on X.

### Documentation

The official documents build on each other, so read them in order.

- [000 Philosophy](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/docs/000-philosophy.md) - The attention-first principle and what it asks of the operator.
- [001 Domain Model](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/docs/001-domain.md) - The flow of work, the core concepts, the concepts that were rejected, and a glossary.
- [002 Authorization](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/docs/002-authorization.md) - How a Trigger becomes work: admission, accept modes, rules, and policy versions.
- [003 Execution](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/docs/003-execution.md) - Ticket stages, the Executor, merging, and failure recovery.
- [004 Prompts](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/docs/004-prompts.md) - What a team writes, how prompts are assembled, and their order of precedence.
- [005 Panel](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/docs/005-panel.md) - The web panel, its tabs and settings, built to show only what needs a person.
- [006 Deployment](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/docs/006-deployment.md) - Manual setup, accounts, configuration, upgrades, and troubleshooting.
- [007 Architecture](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/docs/007-architecture.md) - Core classes, modules, persistence, configuration reload, and open questions.
- [008 Cookbook](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/docs/008-cookbook.md) - A walkthrough of adding a new Source.

### Prompts and Skills

- [Prompts](https://github.com/deepseek-ai/dsh-superagent-prototype/tree/main/prompts) - The admission, dispatch, work, reply, and handoff prompts the Router and Workers follow.
- [Team prompt sections](https://github.com/deepseek-ai/dsh-superagent-prototype/tree/main/prompts/team) - The scope, delivery, and communication sections a team edits.
- [GitHub skill](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/skills/dsh-superagent-github/SKILL.md) - How Workers read issues, pull requests, reviews, and CI.
- [Feishu skill](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/skills/dsh-superagent-feishu/SKILL.md) - How the agent works with Feishu.

## DeepSeek Harness

SuperAgent runs as a profile of DeepSeek Harness (`dsh`), DeepSeek's open-source, plugin-based agent harness.

- [deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) - The official Harness repository.
- [DeepSeek Harness](https://www.deepseek.com/en/harness/) - The official product page.
- [Documentation](https://deepseek-harness.github.io/deepseek-harness/) - The official Harness documentation site.
- [@deepseek-ai/dsh](https://www.npmjs.com/package/@deepseek-ai/dsh) - The `dsh` CLI on npm, used to launch profiles and manage plugins.
- [Architecture](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/architecture.md) - How Harness is put together.
- [Cordis tutorial](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/cordis-tutorial/index.md) - Learn the plugin framework Harness and SuperAgent are built on.
- [Extension cookbook](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/cookbook/extension-cookbook.md) - Recipes for extending Harness.
- [SAFETY.md](https://github.com/deepseek-ai/deepseek-harness/blob/master/SAFETY.md) - The Harness safety notes.

## Guides and Tutorials

- [dsh-superagent-setup](https://github.com/hhse/dsh-superagent-setup) - A Codex and Harness skill with a tested runbook, including setup pitfalls that are not obvious from the docs.
- [Router–Worker Multi-Agent Architecture](https://agentspulse.github.io/tutorials/deepseek-super-agent-architecture/) - A tutorial on how the Router, Workers, and event routing fit together.
- [Prototype Setup, Workflow and Security](https://aicybr.com/blog/deepseek-dsh-superagent-prototype-setup-security) - A walkthrough of requirements, the authorization model, and host-security limits.
- [learn-deepseek-super-agent](https://github.com/aicoder2048/learn-super-agent) - An interactive nine-lesson course on the design article, with simulations, quizzes, and an AI tutor, in Chinese.
- [Super-agent Architecture and Prototype Walkthrough](https://eogee.com/article/302) - A hands-on run of the prototype on WSL2, with native-Windows failures, China mirrors, and a pitfalls table, in Chinese.
- [Observe CI Before Repair](https://www.datacamp.com/tutorial/deepseek-superagent-tutorial) - A DataCamp tutorial that runs a CI-repair rule in observe mode, authorizes one fix, and checks the pull request against a holdout test suite.

## Deep Dives and Analysis

- [Super-agent Design Explained](https://kingy.ai/blog/deepseek-super-agent-design-explained/) - A long read on the architecture, the experiments, and the open problems.
- [One Router, Many Workers](https://cellcog.ai/blog/deepseek-super-agent/) - Why the Router never does the work itself, and what the test numbers mean.
- [The Always-On Router and Worker Design](https://www.developersdigest.tech/blog/deepseek-dsh-superagent-router-worker-always-on-agent-2026) - A developer-focused overview of the always-on design.
- [What It Actually Is, and What It Is Not Yet](https://dev.to/paullovelace/deepseek-super-agent-a-proactive-open-source-coding-agent-prototype-what-it-actually-is-and-438a) - A grounded look at the prototype's current scope.
- [49-chart visual analysis](https://github.com/ruijh/dsh-superagent-prototype-analysis) - Interactive charts of the codebase, data model, and prompts, in Chinese ([live site](https://ruijh.github.io/dsh-superagent-prototype-analysis/)).
- [Independent evaluation](https://github.com/pans1es/superagent-prototype-evaluation) - An unofficial benchmark of 75 runs comparing the two-layer design with a single session, with data and a bilingual report.
- [super-agent-open-questions](https://github.com/FranciscoLaurent/super-agent-open-questions) - Proposed answers to the design article's four open questions, with small simulation experiments, in Chinese.
- [I Ran dsh-superagent End to End](https://dev.to/geekcoding101/i-ran-deepseeks-dsh-superagent-end-to-end-a-hands-on-deep-dive-a29) - A hands-on run on macOS with setup gotchas, three ticket scenarios, and a code-level look at the two-layer authorization.
- [dsh-superagent-anatomy](https://github.com/HY-love-sleep/dsh-superagent-anatomy) - A source-level trace of how a Feishu message becomes a Worker task, with commit-pinned code links, a glossary, and an interactive flow animation, in Chinese.

## Security

- [Execution](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/docs/003-execution.md#execution-variables) - The official note that command wrappers set defaults and are not a security boundary.
- [Deployment](https://github.com/deepseek-ai/dsh-superagent-prototype/blob/main/docs/006-deployment.md#permissions-and-isolation) - The official permissions and isolation notes, including why the agent needs a dedicated OS account.
- [Proactive Coding Agent Security](https://agentbeam.com/blog/deepseek-super-agent-proactive-coding-agent-triggers-security) - How Triggers and Mandates work, and where prompt injection fits.
- [Coding agent that watches team chats](https://www.helpnetsecurity.com/2026/11/02/deepseek-dsh-superagent/) - Help Net Security's coverage of the release and its risks.

## Tools and Extensions

### Sources

A Source is where SuperAgent hears about work. The official bundle ships GitHub and Feishu.

- [dsh-superagent-inbox](https://github.com/JHOpenDev/dsh-superagent-inbox) - A local file-inbox Source that runs SuperAgent with no external accounts.
- [superagent-imessage](https://github.com/wiva-hq/superagent-everywhere) - Ask for work in iMessage and get the pull request back in the same chat.
- [dsh-superagent-redmine](https://github.com/billbill2012/dsh-superagent-redmine) - A Redmine Source that turns issues and comments into Tickets, passes image attachments to the model, and replies as Redmine notes.
- [gh-gitlab](https://github.com/hoogte-oile/gh-gitlab) - A `gh`-compatible CLI that translates the GitHub Source's API calls to GitLab, so an unmodified SuperAgent can watch a GitLab project, documented in Chinese.
- [dsh-super-chat](https://github.com/gekailin/dsh-super-chat) - A chat panel and Source that turns tagged messages into Tickets, with SQLite storage and an optional WeChat bridge.

### Panels and UI

- [dsh-superagent-panel](https://github.com/deepseekv41flash/dsh-superagent-panel) - Embeds the full SuperAgent panel in the DSH NEXT desktop app.
- [dsh-superagent-bridge](https://github.com/deepseekv41flash/dsh-superagent-bridge) - The service-side companion that serves the panel as a standalone page.
- [dsh-superagent-manager](https://github.com/Aily-DSH/dsh-superagent-manager) - A Windows Harness plugin that creates, runs, and embeds several SuperAgent instances in one client, one tab per project, documented in Chinese.
- [dsh-superagent-ui](https://github.com/hustnn/dsh-superagent-ui) - A local operator console with a ticket board, calibration of the agent's judgments, policy and prompt editors, and health views, with a demo-data preview.

### Ports

- [dsh-superagent-windows](https://github.com/Check-mj/dsh-superagent-windows) - A Windows adaptation with a desktop app, multiple instances, a Watchdog, and Router sharding.
- [dsh-superagent-win](https://github.com/buyou-claw/dsh-superagent-win) - A Windows port that scopes the agent identity to each Worker command.
- [pi-superagent](https://github.com/aicodewith-team/pi-superagent) - A port to the pi coding agent that works with any model pi supports.
- [claude-superagent](https://github.com/lyra-planet/claude-superagent) - A port to Claude Code through the Claude Agent SDK that keeps the upstream domain core, with a terminal Source and hook-enforced Worker rules.

### Forks

Independently maintained forks of the prototype with substantial changes of their own.

- [open-superagent](https://github.com/chunonesoft/open-superagent) - Adds self-hosted GitLab and DingTalk Sources, chat-only deployments, and regular upstream merges, documented in Chinese.
- [dsh-superagent-channels](https://github.com/baojingyu/dsh-superagent-channels) - Adds GitLab, Yunxiao Projex, WeChat, DingTalk, and WeCom Sources, and several instances of one channel, installed next to the official bundle.
- [multi-superagent](https://github.com/pprp/multi-superagent) - Runs several isolated repositories in one Harness profile, each with its own Sources, Policy, state, and panel view, documented in Chinese.
- [dsh-superagent-local](https://github.com/mengzhongjie/dsh-superagent-local) - Takes requests from a main session in each Harness workspace instead of GitHub, with attachments passed to Workers.

### Developer Tools

- [dsh-policy-validator](https://github.com/huanlin-labs/dsh-policy-validator) - An offline linter for Policy settings that catches valid-looking configurations that silently disable rules or open admission, documented in Chinese.
- [superagent-github-mock](https://github.com/huanlin-labs/superagent-github-mock) - An offline GitHub REST mock and `gh` shim that drives the unmodified GitHub Source through replayable scenarios, documented in Chinese.
- [dsh-superagent-docker](https://github.com/leokyler/dsh-superagent-docker) - A Dockerfile and Compose setup with a loopback panel proxy, non-interactive setup, and a self-healing service loop.

### Built on SuperAgent

- [dsh-game-studio](https://github.com/yinhaox/dsh-game-studio) - A Godot 4 game studio kit with extra Sources, Guards, Worker playbooks, and a project template, documented in Chinese.

## Reimplementations

- [nano-dsh-superagent](https://github.com/cjy851096/nano-dsh-superagent) - A small, runnable TypeScript version of the five modules from the design article, with an offline mock model.
- [xys-superagent-prototype](https://github.com/ProfYangShengXu/xys-superagent-prototype) - A Python ticket ledger for agent work in one process and one SQLite file.
- [dsh-super-agent](https://github.com/vicfei/dsh-super-agent) - An executor-agnostic TypeScript take on admission tables, observe mode, and tickets for any CLI coding agent.
- [dsh-superagent-java](https://github.com/yuzhiyang1/dsh-superagent-java) - A Java 21 rewrite aimed at parity with the prototype, with a web console and an acceptance matrix, documented in Chinese.
- [deepseek-super-agent](https://github.com/LofiSu/deepseek-super-agent) - A TypeScript runtime with its own harness that maps each feature of the design article to code and tests, for any OpenAI-compatible model.

## Related Projects

- [dsh-session-superagent](https://github.com/MYCF711/dsh-session-superagent) - A session-level take that watches a repository and wakes one Harness session, without a separate instance.
- [Patchwork](https://github.com/ADWMC/Patchwork) - A coding agent for Harness with verifiable tasks, retrieval, memory, and native SuperAgent support.
- [cc-codex-super-agent](https://github.com/Kevin-Pal/cc-codex-super-agent) - A Router and Worker workflow with Claude Code as the Router and native Codex sessions as Workers.
- [cloud-superagent](https://github.com/konbakuyomu/cloud-superagent) - An adaptation of the dispatch design to Claude Code cloud sessions, with deterministic queue, ticket, and gate CLIs, documented in Chinese.

## Translations

- [Chinese docs](https://github.com/saltapp/dsh-superagent-prototype-cn) - A Chinese translation of the official repository and its documentation.
- [English translation by HMLG](https://x.com/HMLGGGG/status/2116724839977308610) - An unofficial English translation of the design article with redrawn figures.
- [English translation by Teortaxes](https://x.com/teortaxesTex/status/2116551612558709142) - A full machine translation of the article, including the experiment table.

## News

- [DeepSeek Drops Enhanced Coding Agent With Aim to Rival Anthropic](https://www.bloomberg.com/news/articles/2026-11-01/deepseek-drops-enhanced-coding-agent-with-aim-to-rival-anthropic) - Bloomberg.
- [DeepSeek open-sources Super-Agent](https://thenextweb.com/news/deepseek-super-agent-open-source-coding-agent) - The Next Web.
- [DeepSeek Releases Open-source Dsh-superagent Coding Agent](https://dataconomy.com/2026/11/02/deepseek-releases-open-source-dsh-superagent-coding-agent/) - Dataconomy.
- [DeepSeek Proposes Super-Agent Architecture](https://analyticsindiamag.com/ai-news/deepseek-proposes-super-agent-architecture-to-automate-ai-coding-workflows) - Analytics India Magazine.
- [DeepSeek Unveils 'Super Agent' to Run Multiple Tasks at Once](https://en.sedaily.com/international/2026/11/01/deepseek-unveils-super-agent-to-run-multiple-tasks-at-once) - Seoul Economic Daily.
- [DeepSeek Unveils AI 'Super Agent' in Coding Race With OpenAI, Anthropic](https://www.scmp.com/tech/article/3372884/deepseek-unveils-ai-super-agent-coding-race-openai-anthropic) - South China Morning Post.

## Related Lists

- [awesome-deepseek-harness](https://github.com/calderbuild/awesome-deepseek-harness) - Resources for DeepSeek Harness, the platform SuperAgent runs on.

## Contributing

Contributions are welcome. Read the [contribution guidelines](contributing.md) first.
