# Tailscalerdp

This repository contains a GitHub Actions workflow to provision a remote Ubuntu host with Tailscale and XRDP for remote desktop access over Tailscale.

## Usage

1. Add repository secrets:
   - `SSH_PRIVATE_KEY`: private SSH key for remote host access
   - `TAILSCALE_AUTHKEY`: Tailscale auth key with appropriate tags

2. Run the workflow manually from GitHub Actions:
   - Choose either `Setup Tailscale + XRDP` for Ubuntu/Linux hosts or `Setup Windows RDP + Tailscale` for Windows hosts.
   - Set `remote_host` to the remote machine address.
   - Set `remote_user` to the remote login user (`ubuntu` for Linux, `Administrator` for Windows by default).
   - Optionally set `tailscale_hostname`.

3. After completion:
   - Linux hosts will be available via Tailscale and XRDP.
   - Windows hosts will be available via Tailscale and native Remote Desktop.

4. Hostname usage:
   - If `tailscale_hostname` is provided, the machine will register with that hostname in Tailscale.
   - If omitted, the host's OS hostname will be used.
   - You can connect to the machine via `hostname.tailscale.net` from another Tailscale-connected device.

## Notes

- The workflow uses `appleboy/ssh-action` to execute installation commands on the remote server.
- The remote host must accept SSH authentication with the provided private key.
- Ensure the `TAILSCALE_AUTHKEY` is valid and has the correct pre-authorized or ephemeral permissions.
