# Positioning

This guide helps contributors describe SoulFire without promising features or guarantees that the product does not provide.

## Name

Write **SoulFire**, with a capital S and F, in prose.
Preserve exact package names, repository names, commands, and identifiers in code.

## Description

Use this short description:

> Minecraft bots for testing, automation, and development.

Use this description when more context helps:

> SoulFire runs and manages Minecraft bots. Use the app, CLI, SDKs, or visual scripts to control bots and observe their activity.

"Minecraft bot automation platform" is a useful category description for technical audiences.
"Minecraft bot tool" remains understandable in existing material.

## Audience and purpose

| Audience | Reader goal |
| --- | --- |
| Server operators | Test behavior and investigate problems on servers they operate. |
| Developers | Build automation through the SDKs or extend the server through plugins. |
| Automation authors | Coordinate bots through built-in features, code, or visual scripts. |

Describe a concrete activity before listing implementation details.
For example, explain that users can capture a bot's view before discussing the renderer or video codecs.

## Product surfaces

- **SoulFire app:** the graphical interface. Qualify desktop, web, or mobile where the distinction matters.
- **SoulFire server:** the backend that manages bots and exposes the API.
- **SoulFire CLI:** the command-line interface.
- **SoulFire SDKs:** the TypeScript and Python libraries for applications and scripts.
- **Plugin API:** the server extension interface.
- **Visual scripting:** the node-based automation editor and runtime.

Use **Minecraft client** for the game client represented by a bot.
Use **SDK client** for a program's connection to the SoulFire API.

## Claims

Describe the supported behavior and its limits.
State the required version or capability for version-dependent features.
Use "local" and "remote" for location, and "managed" for lifecycle ownership.
Describe restart survival, reconnection, and cleanup separately.

Keep use examples within servers that the user owns or has permission to test.
Avoid claims of universal compatibility, guaranteed bypasses, or unlimited scale.
