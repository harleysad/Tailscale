# Tailsacle

This project is based on the examples from [tailscale-dev/docker-guide-code-examples](https://github.com/tailscale-dev/docker-guide-code-examples) and utilizes [Tailscale](https://tailscale.com/) to create a secure Tailscale server for your Docker network.

## Overview

Tailsacle provides a secure solution for accessing Docker network containers remotely without exposing the server or opening multiple ports. It can be used as a security layer to access your Docker containers from anywhere via Tailscale VPN.

## Environment Variables

- `TS_AUTHKEY`: **(Required)** Auth key generated from the Tailscale admin panel.
- `TS_EXTRA_ARGS`: Additional parameters to pass to the Tailscale startup command.
- `TS_STATE_DIR`: Directory for Tailscale state files (default: `/var/lib/tailscale`).
- `TS_USERSPACE`: Set to `false` to use kernel networking.
- `CONTAINER_FOLDER`: Host folder mapped to the container (default: `container-folder`).

## Example Compose Usage

See [`compose.yaml`](compose.yaml) for a sample Docker Compose configuration.

## Common Tailscale Arguments

- `--accept-routes`: Accepts subnet routes shared by other nodes (use with caution to avoid conflicts).
- `--advertise-routes=10.0.4.0/24`: Exposes the internal Docker network (adjust the subnet as needed).
- `--advertise-exit-node`: Allows this node to serve as an exit node (VPN gateway) for other devices.

## References

- [Tailscale Documentation](https://tailscale.com/kb/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)