# d_permissions.inc

SA:MP Permissions - Control your players with new permissions, now with *d_permissions.inc* you can control who can send a message, use a command or even move!

[Go back to the home page](../README.md)

## How to start to use?

- All of the player permissions are off by default. To give the player certain permissions to do certain things, you need to use `SetPlayerPermissionInteger`.

## List of permissions
These are currently available permissions:

| Permission | Description |
|--------------------------------------|------------------------------------|
| `DEFAULT_PLAYER_PERMISSIONS` | The default SA:MP player permissions! |
| `PLAYER_PERMISSION_SENDMESSAGES` | Toggles the player's ability to send messages in the chat. |
| `PLAYER_PERMISSION_USECOMMANDS` | Toggles the player's ability to use all of the server commands! |
| `PLAYER_PERMISSION_USEDIALOGS` | Toggles the player's ability to respond to dialogs. |
| `PLAYER_PERMISSION_USEVEHICLES` | Toggles the player's ability to enter vehicles. |
| `PLAYER_PERMISSION_BUNNYHOP` | Toggles the player's ability to press `KEY_JUMP` and `KEY_SPRINT` at the same time. |
| `PLAYER_PERMISSION_CBUG` | Toggles the player's ability to exploit the C-bug! (Note that this permission isn't included within `DEFAULT_PLAYER_PERMISSIONS` as we don't want players to exploit bugs.) |
| `PLAYER_PERMISSION_USEWEAPONS` | Toggles the player's ability to use weapons - if the player attempts to have a weapon without a permission, all of his weapons will get resetted. |

## API
### `SetPlayerPermissionInteger`
- You can change player's permission anytime using the following function!

```pawn
SetPlayerPermissionInteger(playerid, PLAYER_PERMISSION_SENDMESSAGES | PLAYER_PERMISSION_USECOMMANDS);
```

**NOTE:** Make sure to use bitwise operators instead of `+`.

### `OnPlayerInsufficientPermissions`
- If the player attempts to do something, without a certain permission to do so, you can let him know using the callback below.

```pawn
public OnPlayerInsufficientPermissions(playerid, missingpermission)
{
	if(missingpermission == PLAYER_PERMISSION_USECOMMANDS)
	{
		SendClientMessage(playerid, 0xFFFFFFFF, "You aren't allowed to use commands!");
	}
	if(missingpermission == PLAYER_PERMISSION_SENDMESSAGES)
	{
		SendClientMessage(playerid, 0xFFFFFFFF, "You aren't allowed to send messages!");
	}
	if(missingpermission == PLAYER_PERMISSION_USEDIALOGS)
	{
		SendClientMessage(playerid, 0xFFFFFFFF, "You aren't allowed to respond to dialogs!");
	}
	return 1;
}
```

### `OnPlayerPermissionIntegerChange`
- To let the staff know when player permissions change, you can use the following callback:

```pawn
public OnPlayerPermissionIntegerChange(playerid, oldpermissions, newpermissions)
{
	printf("Player : %i, oldperms : %i, newperms : %i", 
		playerid,
		oldpermissions,
		newpermissions);
	return 1;
}
```
