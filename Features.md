#summary Features used by this qvm
#labels Featured
# Say Area range #
Lets the admin configure the range of say area.

[Cvars#g\_sayArea](Cvars#g_sayArea.md)
  * Author: _Paradox_ inspired by _Lakitu7_
  * Link: [MGDev commit](http://projects.mercenariesguild.net/projects/mgdev/repository/revisions/1a11410eaccce172aa2b80c2949fa16c96029290)
# Instant Build #
Allows for instantbuilding at ANY time.

[Cvars#g\_instantBuild](Cvars#g_instantBuild.md)
  * Author: _Paradox_
  * Link: [commit](http://code.google.com/p/cqvm/source/detail?r=51)
# Restore given states on reconnect #
Automatically restores players state (mute, denybuild, etc) on reconnect. Ends mute evasions.
  * Author: _Slacker_ and _Tori_
  * Link: [issue](http://code.google.com/p/cqvm/issues/detail?id=19)
# Bleeding spree spec durations #
Integrates Mute/Spec duration with Bleeding spree spectator mode.
  * Author: _Paradox_
  * Link: [commit](http://code.google.com/p/cqvm/source/detail?r=39)
# Mute and Spec durations #
Adds times to the `!mute` and putteam spec commands, as well as adding times to votes.
  * Author: _Critux_ and _Slacker_
  * Link: [issue](http://code.google.com/p/cqvm/issues/detail?id=24)
# Automatic bleedingspree revert #
Automatically reverts any damage done by a bleeding player, when bleedingspree is triggered
  * Author: _Rezyn_
  * Link: [commit](http://code.google.com/p/cqvm/source/detail?r=28)
# Improvement of Allflags, addition of restriction flags #
This makes the behavior of allflags consistent, adds support for . flags, and adds .NOVOTE and .NOCHAT
  * Author: _Rezyn_
  * Link: [commit](http://code.google.com/p/cqvm/source/detail?r=27)
# Inactivity mode #
Controls if a player is moved to spectators or dropped when inactive
[Cvar page](Cvars#g_inactivityMode.md)
  * Author: _Rezyn_
  * Link: [commit](http://code.google.com/p/cqvm/source/detail?r=25)
# Bleeding Spree controls #
Controls if the player is outlawed, kicked, or put on spectators
[Cvar page](Cvars#g_bleedingSpreeKick.md)
  * Author: _Rezyn_
  * Link: [issue](http://code.google.com/p/cqvm/issues/detail?id=20)
# Nobuild #
Allows an admin to define areas of the map that building is disabled in
[More info](Admin_commands#!nobuild.md)
  * Author: _Rezyn_ and _Google_
  * Link: [issue](http://code.google.com/p/cqvm/issues/detail?id=21)
# Mark improvements #
Allows for control over the behavior of Mark Decon

[Cvars#g\_markDeconstructMode](Cvars#g_markDeconstructMode.md)
  * Author: _Slacker_
  * Link: [patch](http://code.google.com/p/cqvm/issues/detail?id=17)
# !invisible #
Allows an admin to become invisible, not showing to other players

[Commands#!invisible](Admin.md)
  * Author: _Critux_, _Slacker_ and _Tori_
  * Link: [patch](http://code.google.com/p/cqvm/issues/detail?id=3)
  * Link: [patch](http://code.google.com/p/cqvm/issues/detail?id=25) (Fixes a few bugs)
# Ban modifications by level #
Prevents bans from being modified by admins of a level lower than that of the original banner.

All console bans are at level 0. This includes kicks
This also adds the field blevel to Admin.dat ban entries
  * Author: _Slacker_
  * Link: [patch](http://code.google.com/p/cqvm/issues/detail?id=18)
# Jetpack Fuel #
  * Author: _Slacker_
  * Link: [patch](http://code.google.com/p/cqvm/issues/detail?id=7)

# Other features #
## Cvars ##
A list of cvars is avalible at [Cvars](Cvars.md)

## Admin Commands ##
A  list of admin commands is avalible at [Admin\_Commands](Admin_Commands.md)

## Other ##
For a complete list of changes, please visit the repo change page
[Repo change page](http://code.google.com/p/cqvm/source/list)