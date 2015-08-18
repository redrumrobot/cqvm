#summary List of Cvars added by this QVM
#labels Featured
For a full list of Cvars, please run `/cvarlist` in your server console.
## g\_sayAreaRange ##
Defines the range of say\_area.
## Values ##
Values are in-game units, and as such, can be difficult to mess with. 1000 is the default behavior
> Accepts any floating point value.
# g\_instantBuild #
Allows for instant building, like devmap, at any time
## Values ##
Accepts any standard boolean value
  * **0**: Off
  * **1**: on
# g\_adminTempMute #
Defines the mute duration for mute votes
## Values ##
Accepts any standard tremulous time values. Common ones are listed below
  * **30**: 30 seconds
  * **1m**: 1 minute
  * **1h**: 1 hour
# g\_adminTempSpec #
Defines the spectator duration for spec votes, as well as the spectator duration if [g\_bleedingSpreeKick](Cvars#g_bleedingSpreeKick.md) is set to mode 2
## Values ##
Accepts any standard tremulous time values. Common ones are listed below
  * **30**: 30 Seconds
  * **1m**: 1 minute
  * **1h**: 1 hour
# g\_inactivityMode #
Controls behavior of automatic inactivity actions.
## Values ##
  * **0**: Default, player is dropped from server
  * **1**: Player is moved to spectators
# g\_bleedingSpreeKick #
Controls the behavior of bleedingspree kicks.
## Values ##
  * **0**: Disabled, just uses normal outlaw
  * **1**: Kicks the player
  * **2**: Moves the player to spectators
# g\_markDeconstructMode #
Changes the behavior of Marked Deconstruct
## Values ##
  * **0**: Uses buildpoints to build structures, then deconns marked structures after there are no more Bp.
  * **1**: Decons marked structures first to build new buildings.

# Other Cvars #
### [Rezyn's QVM Cvars](Rezyn_features.md) ###

  * `g_pollVotes`: Allows you to disable poll votes on the server
    * **default** _1 (enabled)_
    * [patch](http://code.google.com/p/cqvm/issues/detail?id=11)

### Slackers cvars ###
  * Jetpack Fuel
    * [patch](http://code.google.com/p/cqvm/issues/detail?id=7)
    * `mod_jetpackFuel`: Allows you to disable or set jetpack fuel
      * **default** _0 (Off)_
      * **Values** 10.0 + (On)
    * `mod_jetpackConsume`: How many units per second the jetpack consumes.
      * **default** _2 (On)_
      * **Values** 1 + (On) 0 - (Off)
    * `mod_jetpackRegen`: How many units per second the jetpack Regenerates.
      * **default** _3 (On)_
      * **Values** 1 + (On) 0 - (Off)