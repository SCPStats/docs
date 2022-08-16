---
sidebar_position: 2
---

# Rolesync

Rolesync allows you to give a player a role in your server based on their roles in your discord server. For example, you could give anyone who has the `Donator` role in your discord server the `Donator` badge in-game. For rolesync to work, a player must have an [SCPStats Account](https://scpstats.com/signup).

## Basic Usage

The most basic usage of rolesync is giving discord members and boosters badges in-game. First, you must get the name of the in-game badge you want to use (this will be under the `Roles` section in your `config_remoteadmin.txt` file). Next, under the `scp_stats` section in your plugin config, you can set `booster_role` to the role you want to give boosters and `discord_member_role` to the role you want to give discord members.

## Custom Roles

In order to achieve the example at the top of the page (giving donators an ingame role), you first need to figure out the ID of the discord role you require players to have in order to give them the in-game role. You can do this by right-clicking on the role and clicking the `Copy ID` button (if you don't see it, go to the `Advanced` tab in your discord settings, then enable `Developer Mode`). Next, figure out the name of the role you want to give players who have this role (this will be under the `Roles` section in your `config_remoteadmin.txt` file). Next, find the `role_sync` section in your SCPStats config (the `scp_stats` section in your plugin config). You should see something that looks like this:
```yaml
role_sync:
- DiscordRoleID:IngameRoleName
- playtime_20:IngameRoleName
```

Add a new entry (following the template at the top). For example, if the ID of your donator role was `123456789` and your donator role was called `donator`, you would add a new entry that looks like:
```yaml
- 123456789:donator
```

Once that's setup, players wil get automatically receive their in-game roles if they have the correct discord roles.

## Advanced Usage

### Preface

Rolesync has a few advanced options that you can make use of. First, you should understand that rolesync works top-to-bottom. That means that the first applicable rolesync entry will be used, so you should put higher roles first on the list.

### Multiple Rules

Rolesync entries can have multiple "rules". For example, you can require that a user has both the booster role and donator role on discord in order to give them the `boostdonator` role in-game. Due to the above rule, you should put this above both the entries for booster and donator. You can add these multi-rule entries like this:
```yaml
- DiscordID1,DiscordID2:IngameRoleName
```
*(you can add as many rules if you want, this example just has two for simplicity)*

Then, the in-game role will only be given if a user satisfies all the requirements.