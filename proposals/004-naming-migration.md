# Proposal 004: Display-name migration

Status: **Proposed**

This proposal selects a coordinated display-name migration from [Proposal 001](001-product-terminology.md)
and [Proposal 002](002-feature-names.md). The implementation PRs depend on an explicit maintainer decision to accept these names.
Opening or merging a proposal document alone does not approve them. Current guides keep their existing vocabulary until that decision.

## Scope

Use **Project** for the persistent container that owns configuration, bots, scripts, files, access, and metadata.
Its identity and resources remain available while all bots are stopped. The rename adds no process isolation or new ownership boundary.
Use **Fleet** for a selection of bots within a project.
Keep **Bot**, **Minecraft account**, **Bot connection**, and **Minecraft profile ID** distinct.
Use **SoulFire** when referring to the open source product, including contribution prompts, to avoid ambiguity with a user's project.

This migration changes display text and documentation. It preserves API types, wire fields, routes, stored IDs, plugin IDs, settings namespaces, and saved node types.
It introduces no data conversion and does not require users to rewrite existing integrations.

## Product vocabulary

| Existing label | Proposed label | Meaning and compatibility |
| --- | --- | --- |
| Instance | Project | Same persistent container. API and SDK identifiers retain `instance`. |
| Instance settings | Project settings | Same settings page and route. |
| Instance metadata | Project metadata | Same persisted metadata and API. |
| Bot POV | Bot view | Observation and interactive control, when supported. |
| Control lease in app text | Take control / Release control | The lease remains the API concept. |
| Load profile | Import configuration | Existing JSON payloads remain importable. |
| Save profile | Export configuration | Same payload format, with a credential disclosure. |
| Duplicate instance | Create from configuration | Copy the configuration and icon into a new project. |
| Friendly name | Name | Existing `friendly_name` and `friendlyName` fields remain valid. |

Keep **Run on this computer**, **Connect to a SoulFire server**, and **Try the demo** for connection choices.
A SoulFire server and a Minecraft server remain separate objects. A separately managed SoulFire server can run locally.

### Configuration contents

**Create from configuration** copies settings, accounts and their credentials, proxies, persistent metadata, and the icon.
Project and account persistent metadata are included. Scripts, files, permissions, and history are not copied.
The new project belongs to the user who creates it.

**Export configuration** includes account and proxy credentials and account persistent metadata.
The app currently omits project-level persistent metadata from exports. Duplication includes it.
The app must disclose those contents beside the export action. The file is not a complete project backup and must be kept private.
Use **SoulFire configuration (JSON)** in file dialogs and `soulfire-configuration.json` for new downloads.
Keep the existing profile storage directory and accept files with older names.

These descriptions follow the current duplication and serialization behavior. Removing credentials or metadata from copies requires a separate behavior change.

## Feature vocabulary

| Existing name | Proposed display name | Stable plugin or page ID |
| --- | --- | --- |
| Auto Eat | Auto eat | `auto-eat` |
| Auto Respawn | Auto respawn | `auto-respawn` |
| Auto Armor | Auto equip armor | `auto-armor` |
| Auto Totem | Auto equip totem | `auto-totem` |
| Auto Reconnect | Auto reconnect | `auto-reconnect` |
| Auto Jump | Random jump | `auto-jump` |
| Auto Chat Message | Auto chat | `auto-chat-message` |
| Auto Register | Auto login and register | `auto-register` |
| Anti AFK | Anti AFK | `anti-afk` |
| AI Chat Bot | AI chat | `ai-chat-bot` |
| Kill Aura / KillAura | Auto attack | `kill-aura` |
| Captcha Solver | Captcha solver | `captcha-solver` |
| Chat Logger | Chat logger | `chat-logger` |
| Disconnect Logger | Disconnect logger | `disconnect-logger` |
| Client Settings | Minecraft client settings | `client-settings` |
| Client Brand | Client brand | `client-brand` |
| Fake Virtual Host | Handshake host override | `fake-virtual-host` |
| Server List Bypass | Ping before join | `server-list-bypass` |
| Forwarding Bypass | Player forwarding | `forwarding-bypass` |

Describe **Auto chat** as repeated configured messages after a delay. **AI chat** generates replies.
Keep **KillAura** in the Auto attack description and retain legacy plugin IDs in discovery search.
Keep the earlier names **Forwarding Bypass**, **Server List Bypass**, and **Fake Virtual Host** in migration references for existing users.
Descriptions must explain server-dependent behavior without promising a bypass.

## Visual-script vocabulary

| Existing name | Proposed display name | Stable node type |
| --- | --- | --- |
| Debounce | Cooldown | `flow.debounce` |
| On Bot Init | On connection created | `trigger.on_bot_init` |
| On Join | On player ready | `trigger.on_join` |
| Get Bot State | Get movement state | `data.get_bot_state` |
| Select Slot | Select hotbar slot | `action.select_slot` |
| Drop Item | Drop cursor item | `action.drop_item` |
| Print | Log message | `action.print` |
| Pathfind To | Go to position | `action.pathfind_to` |
| Get/Set Session Bot Variable | Get/Set connection variable | `variable.get_session_bot`, `variable.set_session_bot` |
| Get/Set Session Instance Variable | Get/Set project runtime variable | `variable.get_session_instance`, `variable.set_session_instance` |
| Get/Set Persistent Bot Variable | Get/Set persistent bot variable | `variable.get_persistent_bot`, `variable.set_persistent_bot` |
| Get/Set Persistent Instance Variable | Get/Set persistent project variable | `variable.get_persistent_instance`, `variable.set_persistent_instance` |

Connection variables belong to one bot connection. A new connection starts without these temporary values.
Project runtime variables remain available while bots stop and start, and reset when the SoulFire server restarts.
Persistent variables use saved project or bot-account metadata.

Keep every previous display name as a search keyword. Keep explicit labels in saved graphs, including labels chosen by their authors.
**Go to position** makes the destination clear in a node palette. It refines the shorter **Go to** proposed in Proposal 002.

## Rollout and acceptance

1. Record an explicit maintainer decision for these display names and link it from this proposal.
2. Merge the server PR for metadata, settings labels, CLI help, compatibility tests, and SDK documentation.
3. Merge the app PR for source English, demo labels, configuration dialogs, and SDK agent prompts.
4. Review updated strings through Crowdin. Other locales keep their current translations until review is complete.
5. Update user documentation and screenshots for the coordinated release, with the old-to-new mappings available to existing users.

The server owns built-in feature and node labels. Clients connected to older servers can still show the earlier names.
Raw API errors can still say **Instance** when they refer to existing identifiers or validation contracts.
The source English app strings change first. Plugin labels supplied by the server remain untranslated, as they are today.
The implementation PR descriptions list their related PRs, checks, and translation status.

Acceptance requires unchanged identifiers and placeholders, import of existing configuration files, resolvable saved node types,
legacy search terms, matching demo labels, and passing checks in the owning repositories.
Update the current glossary and guides only after the decision is accepted. Record implementation and release separately from acceptance.

## Deferred work

- **Preset** needs a defined reusable configuration object. This migration uses import/export configuration for the existing file operations.
- SDK type and architecture changes, including `BotObservation`, `InstanceRuntime`, `bot.world`, and provisioning method renames, need separate compatibility proposals.
- Independent plugin-package display-name metadata and plugins without settings pages need a separate API design review.
- Colors, typography, layout, onboarding behavior, and the interface system remain under [Proposal 003](003-interface-system.md).

## Behavior references

- [Duplication](https://github.com/soulfiremc-com/SoulFire/blob/40377571ed2e8320fde39569d5962b05fabe1ea7/mod/src/main/java/com/soulfiremc/server/grpc/InstanceServiceImpl.java)
- [Configuration contents](https://github.com/soulfiremc-com/SoulFire/blob/40377571ed2e8320fde39569d5962b05fabe1ea7/mod/src/main/java/com/soulfiremc/server/settings/lib/InstanceSettingsImpl.java)
- [Project metadata loading](https://github.com/soulfiremc-com/SoulFire/blob/40377571ed2e8320fde39569d5962b05fabe1ea7/mod/src/main/java/com/soulfiremc/server/InstanceManager.java)
- [Configuration serialization](https://github.com/soulfiremc-com/SoulFireClient/blob/45761469ad665fcba0aac23c1602ec04656d43de/src/lib/profile-file.ts)
