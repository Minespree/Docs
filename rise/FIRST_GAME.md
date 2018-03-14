# Creating your first game

Rise is the game engine that is used to create all the minigames on the network, it is a very capable, flexible and easy to learn system so once you get the hang of it you should be able to make minigames easily.  

## Gamemode

Gamemode is used to initialize and setup the game, you use `Gamemode#builder()` to obtain `Gamemode.GamemodeBuilder` in order to set up the necessary settings listed below.

* `Plugin plugin`   
  
The `JavaPlugin` of the minigame you are creating.

* `Supplier<GameState> initialGameState`  
  
The state that is started after the waiting state ends, most of the time you should handle player spawning and other initialization here.

* `Function<GameMap, MapData> extraDataLoader` *(Optional)*  
  
Calls the `MapData#create(GameMap)` method that is used to translate any variables such as locations into useable game objects, such as the cores in BlockWars or towers in Clash.  
Look at [Cartographer]() on how to make `GameMap`'s

* `Supplier<SpawnHandler> spawnHandler` *(Optional)*  
  
Controls how players should spawn or respawn, depending on how their `SpawnReason`. 

* `List<Function<Game, Feature>> features` *(Optional)*  
  
Features allow a game to integrate with built-in functionality provided by Rise.

* `List<WaitingState.Extension> waitingStateExtensions` *(Optional)*  
   
An extension is used to add anything game specific to the waiting lobby, such as the block selector in Thimble. 

* `GameRegistry.Type game`  
   
Database name of the game.

* `boolean teamHandler` *(Optional)*  
  
Whether the game is a team game or not.

* `int statisticSize`  
  
The size of the statistics menu in spectator mode.

* `Map<String, StatType> statisticMap`  
  
All the statistics that can be obtained in the game.

* `InformationBook informationBook` *(Optional)*  
  
The information book which is given to every player in the waiting lobby.

* `List<KitExtension> kitExtensions` *(Optional)*  
  
Extensions to kit which add more functionality and allow to interact with the game for kits with cooldowns for example.  

## States

States hold the core parts of the minigames and allow you to easily implement game flow.  
If you extend `BaseGameState` it holds all the variables you may need to use in your game, such as `TeamHandler`, `SpectatorHandler` etc.  
  

`onStart(GameState previous)`  
  
Called when the state is started, passing the previous game state as the parameter.  
  
`onStop(GameState next)`  
  
Called when the state is stopped, passing the next game state as the parameter.  
  
The first state started after the waiting state is the one passed in `Supplier<GameState>` as the initial game state.  
If you want to change state after this you should use `GameStateManager#changeState(GameState)` where `GameStateManager` can be obtained if you extend the `BaseGameState` class or by `RisePlugin#getGameStateManager()`.  

Rise, using the state system follows the order of:

1. No game state - only until the minigame plugin is enabled.
2. Setup state - setups the map, team handler, spectator handler etc.
3. Waiting state - lobby until there is enough players to start the game.
4. Game states - any minigame specific game states.
5. EndGameState - when Game#endGame(BabelStringMessageType, String) is called, it kicks all the players, gets rid of the game data and decides whether there has been enough games played before the server should restart.

## TeamHandler

The team handler contains functions for balancing, obtaining and checking team conditions. Balancing is done automatically when the waiting state ends and you don't need to add teams manually through `TeamHandler#addTeam(Team)` as when you create a new `Team` object it is added by default.  
Teams should be created in the games `MapData` child class which will create new `Team` objects each time the game is played, as teams are destroyed after the game ends.  
  
`Team` objects should use the `ColourData` enum from Cartographer, however you can create your own specific teams if necessary.  
  
Each team needs a `ChatColor colour`, `Color rgbColour`, `BabelMessage name`, `String colourBlindCode`, `short woolColour` and `int slot`. Each of the variables should be self explanatory, however the slot is the slot that is placed in the team menu in the waiting lobby.