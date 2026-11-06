# systemd notes

`feishu-agent-schedule` writes:

- `~/.config/systemd/user/feishu-agent-job@.service`
- `~/.config/systemd/user/feishu-agent-job-<name>.timer`

Useful commands:

```bash
systemctl --user daemon-reload
systemctl --user list-timers 'feishu-agent-job-*.timer'
systemctl --user status feishu-agent-job@<name>.service
journalctl --user -u 'feishu-agent-job@<name>.service' -n 100 --no-pager
```

If the user session is not persistent across logout, enable lingering:

```bash
loginctl enable-linger "$USER"
```

If a job overlaps with itself, the runner's `flock` exits successfully without a second run.
