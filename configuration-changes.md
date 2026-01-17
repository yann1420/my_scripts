# Configuration Changes

## Console settings for Macbook air A1477

Add/change the following to `/etc/default/console`

```
FONTSIZE="16x32"
SCREEN_HEIGHT="50"
```

## configuring SAMBA

`Failed to start smbd.service: Unit smbd.service is masked.`

That error means the Samba service (smbd) has been deliberately disabled (masked), so systemd refuses to start it.A masked service is symlinked to /dev/null, which prevents it from being started manually or automatically. This is stronger than just “disabled”.
Fix: Unmask and start smbd
1. Check service status (optional)
```systemctl status smbd```

2. Unmask the service
```sudo systemctl unmask smbd```

If you also use nmbd or winbind, unmask them too:

```sudo systemctl unmask nmbd```

```sudo systemctl unmask winbind```

3. Enable the service (start at boot)
```sudo systemctl enable smbd```

4. Start the service
```sudo systemctl start smbd```

5. Verify it’s running
```systemctl status smbd```
You should now see:
```Active: active (running)```
6. If it still fails
Check logs for configuration errors:
```journalctl -xeu smbd```
7. Also verify your Samba config:
```testparm```
