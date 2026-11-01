# Writing

Write for people who want to understand a feature, complete a task, or recover from an error.
Use clear technical English and a natural, conversational voice.

## Voice

- Use active voice and concrete verbs.
- Keep paragraphs short and focused on one topic.
- Explain a feature through its behavior before its implementation.
- Use the same term for the same concept.
- Explain unfamiliar acronyms on first use.
- Avoid em dashes, filler, exaggerated claims, and repeated exclamation marks.

Technical instructions benefit from short sentences and one action per step.
Product descriptions can use a more natural rhythm. They do not require controlled-language compliance.

## Interface text

Use sentence case. Preserve the spelling of product names and identifiers.
Label an action with its result: **Save changes**, **Start bots**, or **Take control**.
Keep labels concise. Put necessary detail in a nearby description.

| Situation | Example |
| --- | --- |
| Progress | Starting bots... |
| Success | Bots started. |
| Empty state | No bots yet. Add a Minecraft account to create your first bot. |
| Error | Could not connect to the SoulFire server. Check the URL and try again. |
| Permission restriction | You do not have permission to start bots in this instance. |

Do not promise success before the system reaches the named state.
For example, **Start requested** and **Bot ready** describe different results.

## Instructions and documentation

State prerequisites before the step that needs them.
If an instruction has a condition, put the condition first.
Use numbered lists for ordered procedures and bullets for parallel choices.
Use descriptive link text and language tags on fenced code blocks.

Keep tutorials, task guides, reference material, and explanations focused on their separate reader goals.
Keep installation procedures and API details in their owning repositories.
Link to the shared [terminology](terminology.md) instead of duplicating its definitions.

## Errors and limits

State what failed, then give a useful next action.
Include a cause only when the system knows it.
Distinguish permission errors, unsupported capabilities, invalid input, and connection failures.
State which operation a timeout limits.

Avoid **durable**, **persistent**, **isolated**, or **real-time** without the relevant lifetime, boundary, or timing guarantee.
State whether work survives caller disconnection, bot reconnection, or server restart.
Keep exact error messages and API identifiers unchanged inside quotations and code.

## Translation

Keep one meaning per label and give translators the relevant context.
Use explicit units and plural forms.
Keep complete messages together instead of assembling fragments with different grammatical roles.
Preserve technical identifiers across translations.
