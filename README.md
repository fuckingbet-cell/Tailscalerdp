# Tailscalerdp

This repository contains a GitHub Actions workflow to provision a remote Ubuntu host with Tailscale and XRDP for remote desktop access over Tailscale.

## Usage

1. Add repository secrets:
   - `SSH_PRIVATE_KEY`: private SSH key for remote host access
   - `TAILSCALE_AUTHKEY`: Tailscale auth key with appropriate tags

2. Run the workflow manually from GitHub Actions:
   - Select `Setup Tailscale + XRDP`
   - Set `remote_host` to the remote machine address
   - Set `remote_user` to the SSH username (default: `ubuntu`)
   - Optionally set `tailscale_hostname`

3. After completion, the remote host should appear in your Tailscale network and XRDP should be enabled.

## Notes

- The workflow uses `appleboy/ssh-action` to execute installation commands on the remote server.
- The remote host must accept SSH authentication with the provided private key.
- Ensure the `TAILSCALE_AUTHKEY` is valid and has the correct pre-authorized or ephemeral permissions.
