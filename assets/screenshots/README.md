# Interface screenshots

These images support [Proposal 003](../../proposals/003-interface-system.md). They are examples for a proposal. They are not logo assets or marketing images, and they do not show a release.

| File | Screen |
| --- | --- |
| [client-launcher-desktop.png](client-launcher-desktop.png) | Connection choices. |
| [client-launcher-failed.png](client-launcher-failed.png) | Local server startup failure. |
| [client-firstbot-review.png](client-firstbot-review.png) | First-bot review step. |
| [client-overview-fleet.png](client-overview-fleet.png) | Instance overview with bots in different states. |
| [client-settings-discover.png](client-settings-discover.png) | Plugin discovery. |
| [client-botview-failed.png](client-botview-failed.png) | Bot with a failed connection. |
| [client-script-blank.png](client-script-blank.png) | Empty script. |

## Provenance

Each image is a capture of the real client UI, reduced to half size. The original capture used a 1440 pixel wide viewport at 3× scale.

- Client source: uncommitted changes on top of SoulFireClient commit `47356061c89ddd07ae48bc9e98f225a59a4063fb`.
- Data: a temporary local gRPC-Web test server with invented bot names and the reserved `example.test` domain.
- Desktop states: the Electron API was replaced with a test double, and no real server process started.

The images contain no real accounts, addresses, or credentials. [sources.json](../sources.json) records each file's SHA-256 checksum.

## License

The repository [license](../../LICENSE) applies. These images add no new license or trademark policy.
