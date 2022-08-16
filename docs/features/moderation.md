---
sidebar_position: 1
---

# Moderation

SCPStats includes many features to aid in server moderation. Below is a list of them, as well as how to set them up.

## Bansync

At its core, bansync allows you to sync bans between all of your servers. For example, if a player is banned on server #1, they will also be banned on server #2. Setting up bansync is easy, simply go to your SCPStats config (the `scp_stats` section in your EXILED config) and set `sync_bans`, `disable_basegame_bans`, and `link_ips_to_bans` all to `true`. That's it for syncing bans across all of your servers, but there are a few more features that you might find useful as well.

## Warnings

SCPStats includes a system for issuing warnings to players (as well as adding notes to a player for other staff to read). Warnings can be managed through the following Remote Admin commands:

| Usage                  | Permission               | Description                                                                            |
|------------------------|--------------------------|----------------------------------------------------------------------------------------|
| `warn <id> [message]`  | `scpstats.warn`          | Warn a person (with an optional message).                                              |
| `swarn <id> [message]` | `scpstats.warn`          | Silently warn a person (without telling them that they've been warned).                |
| `note <id> [message]`  | `scpstats.warn`          | Add a note to a player.                                                                |
| `warnings <id>`        | `scpstats.warnings`      | View all of a player's warnings.                                                       |
| `deletewarning <id>`   | `scpstats.deletewarning` | Delete a specific warning by its ID (you can view the ID with the `warnings` command). |

Warnings can allow you and your staff to keep track of a player's previous offences and gauge the severity of a punishment based on them. However, using commands may be cumbersome for staff (and can only be used while on the server), so it may be easier and more convenient to use the [SCPStats Panel](https://panel.scpstats.com) (more info below).

## SCPStats Panel

The [SCPStats Panel](https://panel.scpstats.com) can be used to help you manage your bans, warnings, and reports online. It can be accessed by going to [https://panel.scpstats.com](https://panel.scpstats.com) and clicking on your discord server (if you don't see your server, try logging out and back in again). You can explore all the panel's features here, but you'll need to do a bit more setup for your staff to be able to as well. Before you continue, make sure you've setup [Bansync](#Bansync), as the ban management part of the panel won't work without it. In order for your staff to be able to view and use the panel, you must give them permission to do so. Permissions can be given with the `/staffpermissions` command on discord (specially `/staffpermissions <@role> add <permission>`). Permissions are attached to a role, and any person with that role will get its permissions. Here is the list of permissions which you should give out to your staff:

| Permission       | Description                                           | Recommended Position |
|------------------|-------------------------------------------------------|----------------------|
| `players`        | View a list of players who have played on the server. | All Staff            |
| `warnings`       | View the list of warnings.                            | All Staff            |
| `warn`           | Issue a warning.                                      | All Staff            |
| `ban1d`          | Ban for up to one day.                                | Moderator            |
| `ban`            | Ban for any duration.                                 | Moderator+           |
| `unban`          | Unban any ban.                                        | Admin                |
| `deletewarnings` | Delete any warning/ban.                               | Admin+               |

### Showing the Panel In-game

The SCPStats panel can be accessed in-game by adding a few options to your `config_remoteadmin.txt`. This will allow staff members to access the panel through the Remote Admin console, as well as allowing easy lookup of a player's previous offences. To do this, add the following lines to `config_remoteadmin.txt`:
```yaml
external_player_lookup_mode: fullauth
external_player_lookup_url: https://panel.scpstats.com/slauth/DISCORD_ID
external_player_lookup_token: SECRET
```

Make sure to replace `DISCORD_ID` with the ID of your discord server, which can be accessed by right-clicking on your discord server and clicking the `Copy ID` button (if you don't see it, go to the `Advanced` tab in your discord settings, then enable `Developer Mode`). Replace `SECRET` with your server's secret, which can be viewed on the [SCPStats Panel](https://panel.scpstats.com/myservers) by clicking the `View Secret` button under your server.