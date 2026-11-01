# Proposal 001: Product terminology

Status: **Proposed**

This proposal captures the initial naming review. It does not authorize changes to released names or identifiers.

## Instance to Project

An instance holds persistent configuration and independently controlled bots.
It also scopes scripts, files, access, and metadata.
The name can suggest a running process or an individual Minecraft client.

**Project** better describes a persistent automation setup that remains useful while all bots are stopped.
Keep the current boundary and propose a product-level rename.

| Alternative | Tradeoff |
| --- | --- |
| Instance | Preserves familiarity and compatibility, but needs an explanation of what it represents. |
| Project | Covers the persistent automation setup and its supporting resources. |
| Fleet | Describes the bots, but leaves scripts, files, and access unexplained. |
| Session | Suggests a temporary activity. |
| Workspace | Suggests a broader collaboration container. |

The migration needs a shared glossary entry, UI labels, examples, and an explicit API plan.
Existing `instance_id` fields and SDK methods remain valid until a compatibility decision addresses them.
The rename does not add process isolation or change the current destination scope.

## Connection choices

The app currently offers **Integrated server (local)** and **Dedicated server (remote)**.
Its dedicated-server example uses a localhost URL.
An independently managed server can run on the same device.

Proposed actions:

- **Start locally:** the app manages a SoulFire server on this device.
- **Connect to an existing server:** enter a URL and authenticate, whether the server is local or remote.
- **Try the demo:** open the demo connection.

Keep dedicated-server terminology for the standalone distribution where it helps technical readers.
Describe app-managed, SDK-managed, embedded, and separate-process arrangements independently.

## Views and configuration

| Current label | Proposal | Reason |
| --- | --- | --- |
| Bot POV / Bot view | Bot view | Covers video, audio, screens, and interactive input. |
| Control lease in user text | Take control / Release control | Names the user action. The API can retain lease terminology. |
| Profile for reusable configuration | Preset | Avoids confusion with Minecraft profiles. |
| Profile file import/export | Import configuration / Export configuration | Describes the data and does not imply a complete backup. |
| Friendly name | Name | A second qualifier adds no value without a separate technical name. |
| Duplicate instance | Create from configuration | Current duplication excludes scripts, files, permissions, and history. |

## Migration questions

- Does Project fit the intended future ownership and destination scope?
- Does duplication need a more complete operation, a more precise label, or explicit options?
- Which releases can coordinate app, server, SDK, CLI, and documentation updates?
- Which public identifiers need a versioned migration, and which can retain their existing spelling?
- Which translated labels and external integrations depend on the old vocabulary?

## Evidence

- [Instance boundary](https://github.com/soulfiremc-com/SoulFire/blob/4a3048001638243b5528aaf64a0eda35f81f48b2/mod/src/main/java/com/soulfiremc/server/InstanceManager.java)
- [Duplication contract](https://github.com/soulfiremc-com/SoulFire/blob/4a3048001638243b5528aaf64a0eda35f81f48b2/proto/src/main/proto/soulfire/instance.proto)
- [App connection labels](https://github.com/soulfiremc-com/SoulFireClient/blob/5602538de1022679f0f9f86d38eb00543642c9ee/locales/en-US/login.json)
- [App navigation labels](https://github.com/soulfiremc-com/SoulFireClient/blob/5602538de1022679f0f9f86d38eb00543642c9ee/locales/en-US/common.json)
