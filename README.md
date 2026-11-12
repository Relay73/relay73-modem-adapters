# Relay73 Modem Adapters

Integration interfaces connecting Relay73 applications and gateways to independent digital modem implementations.

> **Status:** Repository scaffold. API boundaries and existing adapter code are being organized for migration; this repository does not currently ship a modem.

## Purpose

The project needs to support multiple modems without duplicating their RF protocol implementations or forcing every application to know every modem's internal details.

## Intended responsibilities

- Define host-facing data, control, lifecycle, and diagnostics interfaces.
- Adapt supported modem transports into those interfaces.
- Keep platform-specific audio, PTT, serial, and process controls at clear boundaries.
- Report capabilities to apps, gateways, and station discovery services.
- Provide interoperability tests for new adapters and upstream updates.

## Initial integration targets

| Integration | Direction |
| --- | --- |
| Modem73 | Work with upstream RF transport and KISS interfaces |
| AX.25 packet | Integrate existing packet TNC/KISS solutions where appropriate |
| Official VARA FM | Support installed vendor software through documented interfaces |

A planned integration is not a claim of interoperability or inclusion of third-party software in this repository.

## Design rules

- **Upstream first:** Avoid unnecessary forks and protocol reimplementations.
- **Protocol ownership:** Let the underlying modem handle its own framing, timing, retries, and link mechanics where applicable.
- **No proprietary redistribution:** Respect external software licenses.
- **Tests before claims:** Verify packet exchange, disconnect behavior, and real RF cases in addition to simple compilation.

## Initial milestones

1. Write the adapter interface contract and capability model.
2. Document lifecycle and radio ownership boundaries.
3. Migrate Relay73-owned Modem73 integration code without copying third-party sources unnecessarily.
4. Define AX.25 and other adapter targets as their requirements are established.
5. Add conformance tests in [relay73-rf-lab](https://github.com/Relay73/relay73-rf-lab).

## Related repositories

[Project hub](https://github.com/Relay73/Relay73) | [iOS](https://github.com/Relay73/Relay73-ios) | [Gateway](https://github.com/Relay73/relay73-gateway)

Licensing and contribution instructions will be established before source release.
