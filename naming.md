# Naming

Use this guide for new features, public API concepts, and interface labels.
Existing identifiers remain valid until their owning repository ships a migration.

## Name the concept

Choose a name that describes the user's object or action.
Separate the object from its packaging, runtime, and current state.
For example, a plugin can provide an automation that controls a bot connection.

For a new shared concept, document its owner, identity, lifetime, and behavior first.
Reuse a term from the [glossary](terminology.md) when the definition fits.
Propose a glossary change when the definition does not fit.

## Product names and labels

- Use sentence case for headings, navigation, controls, and feature labels.
- Preserve product names and acronyms, including SoulFire, Minecraft, SDK, API, POV, HTTP, and SOCKS5.
- Use a noun for a destination, such as **Bots** or **Minecraft accounts**.
- Use a verb for an action, such as **Start bots**, **Import accounts**, or **Save changes**.
- Keep the same action name in its button, progress message, and result message.
- Qualify ambiguous endpoints: **SoulFire server URL**, **Minecraft server address**, and **Proxy address**.
- Use **Name** instead of **Friendly name** unless a separate technical name exists.

## Deployment

Location, lifecycle ownership, and process arrangement describe different properties.

| Property | Terms |
| --- | --- |
| Location | Local or remote |
| Lifecycle ownership | App-managed, SDK-managed, or independently managed |
| Process arrangement | Embedded or separate process |

A dedicated server can run locally. An SDK-managed server can use a separate process.
Do not treat **dedicated** as a synonym for **remote**.
Current connection-choice labels and proposed replacements appear in [Proposal 001](proposals/001-product-terminology.md).

## Features and plugins

Name a feature for the behavior it provides.
Avoid an outcome claim that depends on a particular server or configuration.
For example, **Ping before join** describes an operation more precisely than **Server list bypass**.
Existing feature labels remain subject to [Proposal 002](proposals/002-feature-names.md).

Keep a stable machine ID separate from the display name.
Display-name changes do not authorize changes to plugin IDs, settings namespaces, permission IDs, or serialized node types.
Give a plugin its own display name, independent of the number of settings pages it contributes.

Describe **loaded**, **enabled**, and **active** separately.
A loaded plugin can provide a disabled feature. An enabled feature can wait without active work.

## APIs and events

Preserve idiomatic naming in each language: camel case in TypeScript and snake case in Python.
Keep object definitions and operation semantics consistent across languages.

For new APIs, use these distinctions:

| Name | Expected meaning |
| --- | --- |
| `create` | Creates a resource under a documented uniqueness policy. |
| `getOrCreate` | Reuses a matching resource or creates one. |
| `start` | Requests the running state. Readiness requires its own guarantee. |
| `waitUntilReady` | Waits for a documented usable state. |
| `observe` | Acquires observation and state updates. |
| `cancel` | Terminates a particular run or task. |
| `release` | Gives up an acquired resource or control lease. |

For existing APIs, document actual behavior before proposing a rename.
Keep IDs, connection epochs, stream epochs, and usernames distinct in parameter names.
Include units in duration and size parameters where the type does not supply them.

Name events for their exact lifecycle boundary.
Connection creation, login completion, and player readiness are separate events.
Avoid a generic **Ready** event without a description of what becomes usable.

## Visual script nodes

Use **On ...** for triggers, **Get ...** for data reads, and an action verb for mutations.
Include the target where ambiguity matters, such as **Select hotbar slot** or **Drop cursor item**.
Keep standard technical meanings for nodes such as debounce, throttle, and cache.
Describe variable ownership and lifetime independently.

## Compatibility

Change public names through a reviewed proposal with an implementation and migration plan.
Keep existing wire fields, package names, stored IDs, and configuration keys stable during a prose-only update.
Record transitional mappings between old labels and new labels.
Remove obsolete compatibility names only through the owning repository's release process.
