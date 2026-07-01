This is an example project that you can use to get started with [BlastBullets2D](https://github.com/nikoladevelops/godot-blast-bullets-2d).

NOTE: The project contains following error: In enemy_ship scripts 	damage_data.is_from_player = True.

While this is incorrect it doesn't currently cause issues and thus slipped through.

It has been modified to contain basic vertical scrolling shmup functionalities by 2Koiraa, please note that I'm new to Godot so implementations might be suboptimal.

Menu system uses this template https://github.com/Maaack/Godot-Game-Template

BG picture made using this free asset pack: https://screamingbrainstudios.itch.io/isotilepack

My Youtube channel: https://www.youtube.com/@2koiraa922

https://www.youtube.com/watch?v=L10sHF4BnLs For more detailed info about BlastBullets2D

If you own assets used in this template and want this template removed, please contact me.

Template explanation:

1.Main scene

->Main node contains the game. Things like menus are not under main node.

->This game works by camera staying still while bg and enemies scroll. It is important for bg,objects,items and enemies all to scroll at the same speed while not in camera so that they arrive in view like they are set up Main scene.

->Player/enemy shoot by using markers that are accessed by code. Example of having more bullet streams than markers is in player code. Add more enemies by duplicating the enemy node and making it local if it's new enemy type.

->When spawning alot of enemies such as popcorn enemy wave using code should be better.

->The Path2D under Main is just example of how to have enemies follow a path.

2.Code

->Bg.gd is for backgrounds. Have the scroll speed be consistant with offscreen enemies, objects and items.

->BulletManager is my custom manager that is used to make the bullet cancelling functionality. It is one of the autoloads defined in Project settings->Globals. It logs shots by enemies and has the screen clear functionalities. clear_ids_by_owner is called by enemies when they scroll low enough that their bullets no longer matter or when player exits the scene by for example going back to main menu. This function clears unused id:s from bullets that never got cancelled.

->If you want to add bullets that aren't intended to be cancelled they don't need to be logged by bulletmanager (for example player bullets)

->Main controls logic related to CanvasLayer

3. Customisation

->For example adding new inputs involves adding them in Project settings->Input map followed by opening res://scenes/menus/options_menu/input/input_options_menu.tscn amd adding them with same naming to nodes InputActionsList and InputActionsTree

->I have left some parts of the menu system that are currently unused. Example of how to animate the menu can be found by downloading the original menu template that has alternative animated menu.

Few possible next steps to take with this template:

->Add leaderboard and direct player there upon running out of lives. I wanted to leave choosing this implementation to the user of the template, since there's so many services to choose from both free and paid. 

->Add sidebars by expanding window through Project setting->Display->window and then realign camera and boundaries in Player.gd and possibly move CanvasLayer elements there

->Add pointblanking. Possible ideas for implementation

	1.Add new collision shapes in player/enemy
	2.Try accessing lifespan of player bullet (I don't know if this works)
	3.Make player shoot additional short lived bullets.
	4.Limit amount of bullets shot by player that can exist simultaniously
	
->Make enemies have additional patterns (possibly not cancellable?) or spawn additional enemies with higher rank.

->Exiting from game to mainmenu sometimes causes a crash, if this issue still persists after making this into a game investigate the reason.
