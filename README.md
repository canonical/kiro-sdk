# Kiro SDK for Workshop

This SDK provides the Kiro CLI for AI-assisted coding within a workshop. It installs the Kiro CLI tools, persists user configurations and credentials on the host inside `/home/workshop/.kiro` to speed up authentication and preserve settings across workshop updates, and configures environment variables on launch.

---

## Reference workshop

A minimal workshop:

```yaml
# workshop.yaml
name: my-kiro-app
base: ubuntu@24.04
sdks:
  - name: kiro
    channel: latest/stable
```

This demonstrates a basic Kiro setup ready for AI-assisted coding inside the workshop container.

---

## Using the SDK

### Prerequisites, project layout

1. No prerequisite SDKs are required.
2. Place your project files in your project directory. Kiro works with any codebase layout.
3. On launch, the SDK configures the system `PATH` to include `kiro-cli`, `kiro-cli-chat`, and `kiro-cli-term`, sets `KIRO_HOME=/home/workshop/.kiro`, and installs a default system prompt to instruct Kiro on containerized environment constraints.

### Start a coding session

Once the workshop is ready, start an interactive terminal session:

```bash
workshop shell
```

From within the workshop shell, you can launch Kiro to start co-coding:

```bash
kiro-cli chat
```

### Authenticate with Kiro

To log in to your Kiro account:

```bash
kiro-cli login
```

Your authentication tokens, settings, and local profiles are saved inside `/home/workshop/.kiro` and are preserved across workshop updates.

---

## Plugs (resources this SDK consumes)

### `kiro-config`

- Interface: `mount`
- Workshop target: `/home/workshop/.kiro`
- Purpose: Preserves Kiro configurations, credentials, and settings between workshop updates. You can also remount this folder to your host's existing `~/.kiro` folder:

  ```bash
  workshop stop my-kiro-app
  workshop remount my-kiro-app/kiro:kiro-config ~/.kiro
  workshop start my-kiro-app
  ```

## Slots (resources this SDK provides)

This SDK doesn't define any slots.

---

## Documentation and guidance

- [Kiro official documentation](https://kiro.dev)
- [Workshop documentation](https://ubuntu.com/workshop/docs/)

---

## Community and support

- Kiro community: [Kiro Discord](https://kiro.dev)
- Please review our [Code of Conduct](https://ubuntu.com/community/ethos/code-of-conduct) before participating.

---

## Contributions

All contributions, including code, documentation updates, and issue reports, are welcome!

- See [CONTRIBUTING](https://github.com/canonical/kiro-workshops-sdk) for guidelines.
- Open issues or pull requests on the [official repository](https://github.com/canonical/kiro-workshops-sdk).

---

## License and copyright

Copyright 2026 Canonical Ltd. and its affiliates. All rights reserved.

Kiro CLI and SDK are licensed under the proprietary [Kiro License Agreement](https://kiro.dev/license/).

Neither you nor any End User will, or will attempt to (a) modify, distribute, alter, tamper with, repair, or otherwise create derivative works of any Content included in the Services or AWS Content (except to the extent such Content is provided to you under a separate license that expressly permits the creation of derivative works).

