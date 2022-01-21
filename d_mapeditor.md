# d_mapeditor.inc

SA:MP Map Editor - edit San Andreas yourself in the game

# How to start to use?

- Look at examples below.

# API (programming interface)

- There are only few functions though. But really important for the system to work, also are really efficient in commands.
## ShowMapEditorMenuToPlayer
- Shows player a dialog with map editor options.
```pawn
 decl Command:mapeditor(playerid, params[])
{
    ShowMapEditorMenuToPlayer(playerid);
    return 1;
}
```
## ShowObjectInfoLabels
- Used to show everyone on the server, in the specified virtual world, object info labels. They contain info about object's ID, object's rotation offset and object's **x, y and z** coordinates!
```pawn
decl Command:labelon(playerid, params[])
{
    ShowObjectInfoLabels(GetPlayerVirtualWorld(playerid));
    return 1;
}
```
## HideObjectInfoLabels
- Used to hide object info labels.
```pawn
decl Command:labeloff(playerid, params[])
{
    HideObjectInfoLabels();
    return 1;
}
```

# Messages from creator

## Warnings

- **d_mapeditor** contains dialog ID definitions. 
Code:
```pawn
#if !defined DETUTILS_DIALOG_MAPEDITOR

#define DETUTILS_DIALOG_MAPEDITOR 1

#endif

#if !defined DETUTILS_DIALOG_MAPEDIT_CREATE

#define DETUTILS_DIALOG_MAPEDIT_CREATE 2

#endif

#if !defined DETUTILS_DIALOG_MAPEDIT_DSTRY

#define DETUTILS_DIALOG_MAPEDIT_DSTRY 3

#endif

#if !defined DETUTILS_DIALOG_MAPEDIT_EDIT

#define DETUTILS_DIALOG_MAPEDIT_EDIT 4

#endif
```
- They can be pre-defined before including the library so the IDs don't mix.
## Notes

- This is in beta stage, please, if you find any issues - report them.