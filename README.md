# Ansible Role: Substrate Node

This role deploys and sets up Substrate Node on a target Virtual Machine.

## Requirements

- Ansible >= 2.7 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) and are listed in the table below.

| Name                                 | Default Value            | Description                                                                   |
| ------------------------------------ | ------------------------ | ----------------------------------------------------------------------------- |
| `substrate_node_setup`               | `true`                   | Node exporter package version. Also accepts latest as parameter.              |
| `substrate_node_version`             | `0.0.9`                  | Version of the release to download and use. Also accepts latest as parameter. |
| `substrate_node_bin_dir`             | `/usr/local/bin/`        | Folder where binary will be put.                                              |
| `substrate_node_bin_name`            | `opportunity-standalone` | Name of the binary and service to use.                                        |
| `substrate_node_validator`           | `false`                  | Whether node is acting as a validator                                         |
| `substrate_node_friendly_name`       | `null`                   | Name which is used by the Telemetry service.                                  |
| `substrate_node_data_dir`            | `/data`                  | Data directory in which chain state will be stored.                           |
| `substrate_node_use_root`            | `true`                   | Whether to use root as a Linux user for permissions/running                   |
| `substrate_node_chain`               | `opportunity`            | Chain to use by the node.                                                     |
| `substrate_node_p2p_port`            | `30333`                  | libp2p port used by the node.                                                 |
| `substrate_node_rpc_port`            | `9933`                   | HTTP RPC port used by the node.                                               |
| `substrate_node_rpc_external`        | `false`                  | Specify if we want to open up HTTP RPC outside of localhost/polkadot.js.      |
| `substrate_node_ws_port`             | `9944`                   | WebSocket port used by the node.                                              |
| `substrate_node_ws_external`         | `false`                  | Specify if we want to open up WebSocket RPC outside of localhost/polkadot.js. |
| `substrate_node_prometheus_port`     | `9615`                   | Specify which port we want to use for Prometheus endpoint.                    |
| `substrate_node_prometheus_disable`  | `false`                  | Specify if we want to disable Prometheus endpoint.                            |
| `substrate_node_prometheus_external` | `false`                  | Specify if we want to open up Prometheus outside of localhost/polkadot.js.    |

### Playbook

Add it to the requirements file:

```yaml
roles:
  - name: substrate_deployer
    src: https://github.com/digitalnativeinc/ansible-role-substrate-deployer.git
    version: 0.0.1
```

Use it in a playbook as follows:

```yaml
- hosts: all
  roles:
    - substrate_deployer
  vars:
    substrate_node_setup: true
    substrate_node_version: latest
    substrate_node_validator: true
    substrate_node_friendly_name: "Standard Validator"
```

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
