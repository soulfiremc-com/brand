# Terminology

This reference defines the current vocabulary for contributors, SDK authors, and documentation writers.
It distinguishes persistent configuration, live connections, observed data, and automation.

## Core objects

| Term | Meaning | Ownership and lifetime |
| --- | --- | --- |
| SoulFire server | Backend that manages bots and provides the API. | Has its own data and process lifecycle. |
| Minecraft server | Game server that a bot joins. | Separate from the SoulFire server. |
| User | Person or authenticated principal with access to SoulFire. | Has permissions on the server and its instances. |
| Instance | Persistent container for configuration and independently controlled bots. | Scopes access, accounts, proxies, scripts, files, and metadata. Exists while bots are stopped. |
| Bot | Configured automated player controlled through SoulFire. | Belongs to an instance and remains the same bot across reconnects. |
| Minecraft account | Authentication material and Minecraft identity used by a bot. | Current account records also store per-bot configuration and persistent metadata. |
| Minecraft profile | Game identity associated with a username and profile UUID. | Distinct from a SoulFire user or configuration export. |
| Bot connection | Runtime for one connection attempt and its live Minecraft client. | Recreated on reconnect. Its connection epoch identifies that runtime. |
| Fleet | Bots addressed together for selection, distribution, or bulk control. | An orchestration view within an instance, not a replacement for the instance. |
| Proxy | Network intermediary that routes a connection. | An entry available through instance configuration. |
| Proxy pool | Collection of proxies available for allocation. | Distinct from the proxy currently assigned to one bot. |
| Plugin | Package that extends the SoulFire server. | Can contribute settings, commands, permissions, RPCs, events, and task providers. |

**Project is a proposal, not the current name for Instance.** See [Proposal 001](proposals/001-product-terminology.md).
An instance is a configuration and permission boundary. The name does not promise process isolation or a security sandbox.

## Identity

The current implementation identifies a configured bot within an instance by its account's profile UUID.
Fields named `bot_id`, `account_id`, and `profile_id` can refer to this same UUID in different APIs.
The instance ID supplies the scope. The profile UUID alone does not identify a bot across all instances.

A provisioning name, Minecraft username, display name, and UUID have different roles.
Document each role instead of using "name" for all four.
Offline and Bedrock identities do not imply a Java online-mode profile UUID.

**Offline authentication** means that the identity does not use online authentication.
**Disconnected** describes the current connection state. An offline-mode bot can be connected.

## Automation

| Term | Meaning | Lifecycle |
| --- | --- | --- |
| Action | One requested operation, such as sending chat or selecting a slot. | Can complete asynchronously. The name does not promise an immediate result. |
| Task | Server-managed work with an ID, status, cancellation, and a result. | Caller-disconnect and bot-reconnect policies control survival. Server shutdown cancels active tasks in the audited implementation. |
| Behavior | Composable SDK logic that coordinates operations for a bot. | Runs in the caller's effect and scope. It can start server tasks. |
| Visual script | Stored node graph that responds to triggers. | Belongs to an instance. An active script can wait without executing a run. |
| Run | One execution of a script trigger or another explicitly named program. | Has an execution lifetime, distinct from the stored program. |
| Trigger | Event or timer that starts a visual script run. | Supplies the inputs defined by that trigger. Not every trigger supplies a bot. |
| Control lease | Time-limited exclusive bot control granted through the API. | Has renewal, expiry, and release rules. |

"Durable" needs an explicit survival guarantee. Use **server-managed task** without a claim of server-restart recovery.
**Automation** describes automatic product behavior. **Plugin** describes how an extension is packaged.

## State and lifetimes

- **Desired state:** persistent operator intent, such as keeping a bot running.
- **Runtime status:** the connection controller's current progress or error.
- **Connection phase:** progress from connection setup through player readiness and disconnection.
- **Snapshot:** observed game data at a point in time.
- **Configuration:** values that control behavior. Individual editable values are settings.
- **Metadata:** namespaced extension data. Its owner and lifetime require an explicit description.

Qualify **session** with its purpose, such as login session or POV control session.
The SDK's `BotSession` represents observation and reduced state. It is distinct from the bot connection.

Current "session bot variables" use connection metadata and disappear on disconnect.
Current "session instance variables" use instance runtime metadata and disappear when that runtime restarts.
Persistent bot and instance metadata survive their corresponding runtime restarts.
Script caches and state machines require their own scope descriptions.

## Views and exports

**POV** means point of view. The interactive feature also carries input, game screens, and optional audio.
**Camera** names the SDK surface for rendered image and frame capture.
An observation stream supplies data. It does not, by itself, grant exclusive control.

Existing **profile** imports and exports contain configuration.
Use **configuration export** when explaining their contents. A profile export is not a complete instance backup.
Renaming existing controls or file formats requires a migration decision.

## Baseline sources

This baseline records source behavior inspected on 2026-11-01. Released versions can differ.

- [Bot identity and lifecycle](https://github.com/soulfiremc-com/SoulFire/blob/4a3048001638243b5528aaf64a0eda35f81f48b2/proto/src/main/proto/soulfire/bot.proto)
- [Account representation](https://github.com/soulfiremc-com/SoulFire/blob/4a3048001638243b5528aaf64a0eda35f81f48b2/mod/src/main/java/com/soulfiremc/server/account/MinecraftAccount.java)
- [Task lifecycle](https://github.com/soulfiremc-com/SoulFire/blob/4a3048001638243b5528aaf64a0eda35f81f48b2/mod/src/main/java/com/soulfiremc/server/task/BotTaskManager.java)
- [Visual script contract](https://github.com/soulfiremc-com/SoulFire/blob/4a3048001638243b5528aaf64a0eda35f81f48b2/proto/src/main/proto/soulfire/script.proto)
- [SDK observation and bot operations](https://github.com/soulfiremc-com/SoulFire/blob/4a3048001638243b5528aaf64a0eda35f81f48b2/sdk/typescript/src/client.ts)
