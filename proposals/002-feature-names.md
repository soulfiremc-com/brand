# Proposal 002: Feature names and lifecycle language

Status: **Proposed**

[Proposal 004](004-naming-migration.md) selects the display-name changes and defines their compatibility and rollout. Other architectural changes remain separate.

These recommendations need a separate decision before implementation.
They preserve plugin IDs and stored node types unless a migration explicitly changes them.

## Built-in features

| Existing feature | Proposed display name | Reason |
| --- | --- | --- |
| Auto Eat | Auto eat | Clear behavior. Apply sentence case. |
| Auto Respawn | Auto respawn | Clear behavior. Apply sentence case. |
| Auto Armor | Auto equip armor | Makes the action explicit. |
| Auto Totem | Auto equip totem | Describes offhand equipment. |
| Auto Reconnect | Auto reconnect | Keep the term and expose it as a connection policy. |
| Auto Jump | Random jump | Distinguishes periodic jumping from Minecraft's obstacle auto-jump. |
| Auto Chat Message | Auto chat | Shorter name for automatic message sending. |
| Auto Register | Auto login and register | Includes both supported actions. |
| AntiAFK | Anti AFK | Keep the familiar term and explain the movement in its description. |
| AIChatBot | AI chat | Avoids a second meaning of bot inside the product. |
| KillAura | Auto attack | Describes behavior. Keep KillAura as a search keyword. |
| Captcha Solver | Captcha solver | Clear behavior. Apply sentence case. |
| Chat Logger | Chat logger | Clear behavior. Apply sentence case. |
| Disconnect Logger | Disconnect logger | Clear behavior. Apply sentence case. |
| Client Settings | Minecraft client settings | Distinguishes the bot's game client from the SoulFire app. |
| Client Brand | Client brand | Keep the Minecraft protocol term. |
| Dialog Handler | Server dialogs | Names the user-facing feature. Handler remains useful internally. |
| Fake Virtual Host | Handshake host override | Describes the field that changes. |
| Server List Bypass | Ping before join | Names the operation without guaranteeing a bypass. |
| Forwarding Bypass | Player forwarding | Use an umbrella name and describe bypass-specific modes explicitly. |
| SDK Example Plugin | SDK example plugin | Keep it in developer discovery, separate from ordinary feature discovery. |

Group features by user purpose, such as connection, automation, logging, and integrations.
Keep **Plugin** for the extension package.
Give each package a display name independent of its settings pages.

## Visual nodes

| Existing node | Proposed display name | Reason |
| --- | --- | --- |
| Debounce | Cooldown | The implementation immediately allows an invocation, then rejects calls during a cooldown. |
| On Bot Init | On connection created | Runs before player readiness and repeats for a new connection. |
| On Join | On player ready | Explains when game actions become usable. |
| Get Bot State | Get movement state | Returns movement and environmental flags rather than the complete bot state. |
| Select Slot | Select hotbar slot | Identifies the slot range and purpose. |
| Drop Item | Drop cursor item | Identifies the item that the operation drops. |
| Print | Log message | Describes the output destination. |
| Pathfind To | Go to | Names the goal. Pathfinding remains the technical description. |

Variable controls need separate owner and lifetime descriptions.
The current session-bot and session-instance variables have different lifetimes.
Label temporary connection data separately from temporary instance runtime data and persistent data.

## SDK and domain boundaries

- Keep Bot, Minecraft account, and Bot connection as distinct concepts.
- Document the current identity key before introducing a separate bot ID.
- Keep account reassignment and shared credential storage as explicit architectural decisions.
- Place world-map data under `bot.world` rather than `bot.camera` in a future API revision.
- Place instance-scoped scripts on the instance API instead of implying administrator-only access through `client.admin`.
- Consider BotObservation for the current SDK BotSession object.
- Separate start intent, observation, readiness, and scope cleanup in operation names and documentation.
- Reconsider `createBot` where it reuses named resources. Keep the idempotent behavior explicit.
- Consider InstanceRuntime for InstanceManager and BotLifecycleController for BotStateManager.

These changes require behavior and compatibility review. Display-name improvements do not require all of these architectural changes.

## Guarantees and lifecycle verbs

Use **server-managed task** for work that survives its caller under the selected policy.
Current active tasks do not survive SoulFire server shutdown.
Avoid an unqualified **durable** promise.

Keep connection creation, login completion, and player readiness separate.
Keep an active script's trigger subscription separate from a run that is executing.
Review enable/disable, activate/deactivate, and pause/resume against their actual persistence and execution behavior.
Reserve pause/resume for operations whose preserved state matches that promise.

## Rollout order

1. Correct misleading descriptions of behavior and survival guarantees.
2. Agree on ownership, identity, and lifetime definitions.
3. Approve display names and feature groups.
4. Update app labels, documentation, examples, and translations together.
5. Change public identifiers only through a compatibility plan.

## Evidence

- [Built-in plugin implementations](https://github.com/soulfiremc-com/SoulFire/tree/4a3048001638243b5528aaf64a0eda35f81f48b2/mod/src/main/java/com/soulfiremc/server/plugins)
- [Cooldown implementation named Debounce](https://github.com/soulfiremc-com/SoulFire/blob/4a3048001638243b5528aaf64a0eda35f81f48b2/mod/src/main/java/com/soulfiremc/server/script/nodes/flow/DebounceNode.java)
- [Visual node implementations](https://github.com/soulfiremc-com/SoulFire/tree/4a3048001638243b5528aaf64a0eda35f81f48b2/mod/src/main/java/com/soulfiremc/server/script/nodes)
- [SDK instance and bot operations](https://github.com/soulfiremc-com/SoulFire/blob/4a3048001638243b5528aaf64a0eda35f81f48b2/sdk/typescript/src/client.ts)
- [SDK administration surface](https://github.com/soulfiremc-com/SoulFire/blob/4a3048001638243b5528aaf64a0eda35f81f48b2/sdk/typescript/src/admin.ts)
- [Task shutdown behavior](https://github.com/soulfiremc-com/SoulFire/blob/4a3048001638243b5528aaf64a0eda35f81f48b2/mod/src/main/java/com/soulfiremc/server/task/BotTaskManager.java)
