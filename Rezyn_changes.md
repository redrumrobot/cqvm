#summary These are the changes ported from Rezyn's QVM
These changes are from [Rezyn's QVM](http://mysite.verizon.net/johne/rezynqvm.html). This readme is from there as well. They are included in their own Wiki document because they are useful to people, but do not reflect work done only to this QVM.

# Changes.txt #

{{{Rezyn's QVM 1.1      - patch list -        June 4, 2009

Tremulous game enhancements and toys for Lakitu7's QVM v 5.5

All these patches combined create the big patch:
> Rezyn\_game\_QVM\_1\_1\_0.patch

These patches are numbered incrementally, applying them in
order of lowest to highest guarantees the easiest path.

Patches that are dependent on other patches or are easier
to apply after another patch are denoted with :
  * requires - patch listed is required to be applied first
  * easywith - patch is not necessary, but conflicts may arise
> > or parts may fail that depend on this patch

Patch Set is for Lakitu7 QVM release 5.5

rez\_a000\_QVM\_1.1\_README.txt

> Overview of features and changes, how to build QVM

rez\_a001\_QVM\_1.1\_CHANGES.txt
> This file

rez\_l010\_lak550\_maplog\_updates.patch
> maplog now logs !restart

rez\_l030\_lak550\_welcome\_message.patch
> g\_welcomeMsg:     Message to display when players connect
> g\_welcomeMsgTime: Time to display the message in seconds

rez\_l040\_lak550\_deconwarn\_info.patch
> Include buildable type when warning players/admins about
> > deconning protected buildables

> Also warn admins that are on spectator, and flood protect message

rez\_l050\_lak550\_verify\_guid\_ip\_ghost.patch
> Add GUID format validation
> Add clientinfo IP string validation
> Add g\_maxGhosts to control max clients from same IP

rez\_l062\_lak550\_flag\_suspendban\_immunity.patch
> Add (f) !flag and !unflag to control flags of fellow (lower) admins
> Add (I) !immunity to give a registered player immunity from IP bans
> > (GUID based bans still apply), uses flag 'W'
> > NOTE: original patch used '&', but that conflicts with
> > > the existing admin\_stealth flag in the Lakitu7 QVM.

> Add (J) !suspendban to temporarily suspend an existing ban
> > == 061 added missing !unflag
> > == 062 added !flaglist to list all flags in the QVM

rez\_l070\_lak550\_adminlog.patch

> Add (A) !adminlog to access admin command and player vote history

rez\_l080\_lak550\_retribution\_percentages.patch
> Scale retribution to each player based on amount of friendly fire
> they deal to a teammate. ( g\_retribution )
> Also cancel retribution when the player completely heals

rez\_l090\_lak550\_tklog.patch
> Add (t) !tklog to log recent teamkill activity

rez\_l100\_lak550\_credit\_overflow.patch
> g\_creditOverflow: Credit overflows onto teammates
> > 0 = off
    1. = distribute to teammates evenly
> > 2 = give to higher ranked teammates first (by score)

rez\_l111\_lak550\_denyweapon.patch

> Add (d) !denyweapon and !allowweapon
> > disable a player's ability to use one or more types
> > of classes or weapons, use 'all' to deny all but the basics
> > == 111 no longer allows denyweapon on self

rez\_l120\_lak550\_demo.patch

> Add (?) !demo to toggle visibility of admin chat
> > (so they are not seen when recording a demo)

rez\_l133\_lak550\_intermission\_map\_votes.patch

> Add intermission map voting, by adding **VOTE** sections to
> the map rotation.
> g\_mapRotationVote: Time in seconds to allow for choosing
> > a map in intermission.
> > default=15

> g\_readyPercent: Percent of players that need to be ready
> > to speed up moving past intermission scoreboard.
> > default=0 (off, old scorboard ready rules apply)


> EXAMPLE vote section for maprotation.cfg:
    * OTE**> > > {
> > > map1
> > > map2
> > > map3
> > > }

> In place of a normal map name, use the special name**VOTE**> followed by a bracketed section that contains up to 8 maps.
> > == 131 fixed false errors on server console
> > == 132 adds top 3 maps indicator and g\_nextMap messages
> > == 133 merged patch #rez\_l440 to update !rotation**

rez\_l143\_lak550\_custom\_votes.patch

> Adds extend votes
> > g\_extendVotesPercent: percent of votes needed to pass
> > > default is 74, 0 disables extend votes

> > g\_extendVotesCount: number time an extend vote can be called
> > > default is 2

> > g\_extendVotesTime: number of minutes to extend timelimit
> > > when extend vote passes
> > > default is 10

> Adds layout votes
> Adds g\_defeatVoteMinTime to set minimum time before which admit
> > defeat votes are not allowed, value is in seconds, default is 60

> Adds percent to pass support to team votes
> Extends g\_allowVote by adding 2 additional settings:
> > 2 = disable team voting
> > 3 = disable team kick votes

> Players can not switch or leave team during a team vote

> Custom votes are now easy:
> g\_customVote1 through g\_customVote8
> > g\_customVote cvars uses a comma delimited format:
> > > "votename,Vote message string,vote pass command[,percent]"
> > > > votename:            name to use with /callvote
> > > > Vote message string: message displayed on screen
> > > > vote pass command:   command run on server when vote passes
> > > > > (semicolons can be used to define multiple commands)

> > > > percent:             percent of votes needed to pass
> > > > > (if percent is not present, uses g\_customVotePercent)

> g\_customVotePercent is the default vote percent needed for
> > custom votes to pass

> == 141 changed flag of listlayouts to same as listmaps (j)
> == 142 merged patch #rez\_p660 to add color, and CP to votes
> == 143 added g\_defeatVoteMinTime and fixed g\_allowVote = 2

rez\_l150\_lak550\_dynamic\_bps.patch
> Adds dynamic build points based on player count
> > g\_dynamicBuildPoints: default=0 (off, use standard bps cvars)
> > > value to add for each player that is joined to a team

> math = DefaultBPS + (TotalPlayersOnBothTeams **g\_dynamicBuildPoints)**

rez\_l161\_lak550\_mark.patch
> Add second mode to marked decon, setting
> > g\_markDeconstruct to 2 will allow the use of /mark to toggle
> > a buildable for deconstruction. reload will also toggle.
> > == 161 Fixed reload toggling mark and protect for aliens

rez\_l170\_lak550\_newbie\_nobuild.patch

> Adds g\_newbieNoBuild, which prints a message to players that have
> > not set a name when they try build or deconstruct a buildable.

> g\_newbieNoBuildMessage will set the message to print, by default
> > includes instructions for setting a name.
      * easywith rez\_l160\_lak550\_mark.patch

rez\_l180\_lak550\_negative\_admin\_levels.patch

> Allow saving of negative admin levels
> update !listadmins to allow listing negative levels
> > (example: !listadmins 1 -1)

rez\_l190\_lak550\_silent\_specme.patch

> add silent option to !specme for admins with !kick permission,
> whereby joining of spectators is not announced to players

rez\_l201\_lak550\_chat\_channels\_seen.patch
> Add chat channels and !seen command
> > /join # 

&lt;password&gt;

: join a channel # with optional password
> > /part #:            leave a channel #
> > /0 /1 ... /8 /9:    talk in a joined channel #

> Adds !seen to look up when a player was last on the server
> > shares admin flag with !listadmins

> == 201 fixed password argument of /join

rez\_l210\_lak550\_expire.patch
> Add (G) !expire command, which resets the 5 oldest
> level 1 admins to 0 if they have not played on the server
> within g\_adminExpireTime days, as reported by !seen.
> Actions must be confirmed with the '!expire confirm' option,
> otherwise matching players are only listed and not expired.
> shares admin flag with !readconfig
    * requires rez\_l200\_lak550\_chat\_channels\_seen.patch

rez\_l222\_lak550\_sprees\_outlaw.patch
> Add sprees and !outlaw
> > g\_killingSpree:  Reward killer of a player that is on a roll
> > g\_bleedingSpree: Base punishes players that hurt teammates/base
> > g\_feedingSpree:  Retard spawn rate for those that feed

> all cvars default to 0 (off)
> > killing and feeding sprees are kills/feeds per minute
> > for bleeding spree, each increment is equivelant to 100 HP
> > > of bleeding team per minute.

> !outlaw (flag 'O') controls a player's bleeding spree value
    * requires rez\_l090\_lak550\_tklog.patch
> > == 221 fixed missing sprees in tklog
> > == 222 fixed deconning inside hovel triggering bleed

rez\_l230\_lak550\_register\_password.patch

> Adds password ability to register, and to specify admin level
> g\_adminRegisterLevel: default 1
> > highest level register will accept  without a password

> g\_adminRegisterAdminLevel: default 0 (off)
> > highest level allowed when using a password

> g\_adminRegisterAdminPass:  the password

rez\_l240\_lak550\_practice\_mode.patch
> Adds ([) !practice: allows setting text, which for players
> with that text in their name can join any team regardless
> of balance.
> Turns off after # of map changes specified on the command.

rez\_l250\_lak550\_free\_credits.patch
> Adds g\_freeCredits cvar, which gives players full credits
> after each death (when they spawn). when the cvar is set
> higher than 1, counts down on each map change then turns
> itself off (0). default is off (0).
    * easywith rez\_l240\_lak550\_practice\_mode.patch

rez\_l262\_lak550\_karma.patch
> Karma, persistents between visits for registered players
> > g\_karma: 0=off (default)
      1. on
> > > 2=on + auto register players with GUID

> karma tries to track how a player contributes or detracts
> from their team. higher karma is 'better'
    * requires rez\_l200\_lak550\_chat\_channels\_seen.patch
    * easywith rez\_l221\_lak550\_sprees\_outlaw.patch
> > == 261 fixed botched port that put random code in wrong function
> > == 262 fixed karma update on map change while player connected

rez\_l270\_lak550\_crazy\_g\_mods.patch

> My crazy g\_mods patch that lets these cvars adjust game balance, most
> require a map change to take effect.
> > g\_modBuildableHealth   Buildable health
> > g\_modBuildableSpeed    Buildable fire rate
> > g\_modBuildableCount    Number of OMs/RCs allowed
> > > ( 0 = normal, 2 or more is enable count OMs/RCs )

> > g\_modHumanStamina      Human stamina
> > g\_modHumanHealth       Human health
> > g\_modAlienHealth       Alien health
> > g\_modAlienRegenRange   Alien regen rate is based on distance from base
> > > ( 0 = normal, 1 = enable )

> > g\_modHumanRate         Human fire rate
> > g\_modAlienRate         Alien fire rate
> > g\_modWeaponAmmo        Weapon ammo per clip
> > g\_modWeaponReload      Weapon reload time
> > g\_modTurretAngle       Allow high turret build angles
> > > ( 0 = normal, 1 = enable )

> > g\_modStage3Strength    Alter stage 3 buildable ( hives and teslas )
> > g\_modMainStrength      Damage/range modifier for Reactor and Overmind

> unless noted, cvar value is in percent of normal.
> 0 is disabled, the default. a value of 100 will offer no change as it
> is 100 percent of normal, 50 would be half and 200 would be twice
> the normal, etc.

rez\_l281\_lak550\_auto\_kick\_revert.patch
> Adds auto kick on excessive team bleeding
> > g\_bleedingSpreeKick, default 0 off
> > (kicks when player goes 20 percent over bleeding spree threshold)

> Adds auto ban when kicked twice within a period of time
> > g\_adminBanRepeatKicks, default 0 off
> > (value is time in hours, this is the time period within which
> > > if a player is kicked twice the original kick will become a ban
> > > and be extended to g\_adminBanRepeatKicks hours)

> Adds auto revert deconned/teamkilled buildables when player is kicked
> > g\_autoRevert, default 0 off
> > (value is number items to revert, must be tk/decon by that player and
> > > within 5 minutes of kick)
      * requires rez\_l221\_lak550\_sprees\_outlaw.patch
      * easywith rez\_l261\_lak550\_karma.patch
> > > == 281 fixed new bans from tripping the repeat kick checker
> > > > and added autorevert to ban

rez\_l291\_lak550\_kickban\_logging.patch

> Logs kicks and bans to games.log
> > == 291 added ip and guid to the log output

rez\_l311\_lak550\_vampire\_SD.patch

> Add Vampire Sudden Death, the cvars:
> > g\_vampireDeathTime  VSD time in minutes, should be after normal SD
> > g\_vampireDeath      VSD is active
> > g\_vampireDeathInfo  text to CP to users default is '!info vampire'

> example !info vampire info-vampire.txt:
> > ---- cut paste ---
<sup>6Vampire Sudden Death</sup>7, explained:
^2 **Both team bases self destruct
^2** Player health slowly decreases
^2 **Damage to enemy goes to attacker as gained health
^2** Damage to teammates gives them your health
^2 **Humans regain free ammo over time
^2** No medkit or alien health regeneration
> > ---- cut paste ---

> == 311 fixed health damage over time and medkit message

rez\_l351\_lak550\_realadminname\_fixes.patch
> fix suspendban to use the registered admin name when
> updating a ban record
> == 351 updated patch for Lakitu7 QVM release 5.5, which
> > fixed adjustban however subnetban was overlooked.

rez\_l360\_lak550\_flexible\_pause.patch

> adds (S) !unpause so that !pause is no longer a toggle
> adds individual pausing of players by name or slot #
> can pause all players with **then unpause specific player
> to undo a decon, etc.**

rez\_l373\_lak550\_fix\_markdecon.patch
> backport most of the markdecon code from (current) svn 1143
> to fix placing of new buildables over marked buildables
    * easywith rez\_l270\_lak550\_crazy\_g\_mods.patch
> > > (the g\_mod patch is not required, however a merge
> > > > conflict will need to be hand resolved without it)

> > == 371 fixed building spawns blocked by marked buildable
> > > and backports fix for killing spawns by building
> > > on top of spawn

> > == 372 cleaned up a corner case error return value
> > == 373 allows g\_markDeconstruct cvar to be changed,
> > > instead of read-only

rez\_l421\_lak550\_buildpoint\_recover.patch

> add Build Point Recovery. When a buildable is killed, it's build
> points are slowly regained for use over time. The rate becomes
> slower with each stage advance of your team.
> > g\_buildPointsRecoverRate sets how many build points to recover
> > > per minute, default is 0 (off, recovery feature is disabled)

> a value of 25 is a good point to start
  * credit to Mercenaries Guild dev team (mgdev) for the whole idea
> == 421 fixed some minor issues

rez\_l450\_lak550\_dcc\_distance\_check\_fix.patch
> fix bug in Defence Computer check when it is far from map origin

rez\_l460\_lak550\_oldstyle\_subnets\_work.patch
> allow old style subnets to work, and fix use of unzeroed memory

rez\_l471\_lak550\_showbans\_color\_expired.patch
> show expired bans in !showbans
> use color to indicate subnets, expired, and suspended bans
> == 471 adds update for unrelated showbans issue

rez\_l480\_lak550\_ban\_log\_warning\_updates.patch
> update admin chat warning to include banned GUID matches

rez\_l490\_lak550\_adjustban\_unban\_update.patch
> extend g\_adminMaxBan to include !adjustban and !unban
> add support of +/- modifier to adjustban

rez\_l500\_lak550\_subnet\_overflow\_fix.patch
> fix overflowing integers in subnet code by making them unsigned

rez\_l510\_lak550\_turret\_aim.patch
> adds /aim to set a turret aim direction when idle
> enable with g\_turretAim, default is 0 (off)

rez\_l520\_lak550\_listadmins\_offset\_fix.patch
> fix offset when using !listadmins admin level search


> -- patches based from p-g-qvm --


rez\_p611\_lak550\_killer\_hp.patch
> Add g\_killerHP cvar to control printing of killer's
> health points when a player dies
> > == 611 fixed color after killer's name

rez\_p620\_lak550\_slap\_drop.patch

> Add (x) !slap to slap players around or unstick them
> Add (X) !drop to disconnect players

rez\_p631\_lak550\_bring.patch
> Add (h) !bring to move to a player's location when spectator
> == 631 fixed bringing to a spectator following a player

rez\_p640\_lak550\_teamstats.patch
> Add g\_teamStatus which allows /teamstatus command to display
> critical information about the team

rez\_p650\_lak550\_chat\_team\_color.patch
> Colorize the team indicators [S](S.md), [A](A.md), [H](H.md) on chat messages.

rez\_p670\_lak550\_bubbles.patch
> Add (q) !bubbles to draw attention to a player


> -- patches that require nearly all of the above patches --


rez\_r531\_lak550\_multichar\_admin\_flags.patch
> merge lakitu7's support for multi character admin flags

rez\_r541\_lak550\_merge\_svn150\_to\_164.patch
> merge fixes from lakitu7 svn from 150 to 164

rez\_r550\_lak550\_popular\_map\_votes.patch
> adds a popular map group:
> > g\_popularMaps             space separated list of maps
> > g\_popularMapsVotePercent  vote percent needed to pass for these maps

> maps list in g\_popularMaps will require g\_popularMapsVotePercent,
> all other maps will use the standard g\_mapVotesPercent.

rez\_r560\_lak550\_vote\_kick\_blame\_minvotes.patch
> kick reason includes who initiated the vote

rez\_r570\_lak550\_g\_idlemapswitch.patch
> adds g\_idleMapSwitch, which when enabled will reduce the timelimit
> when no one is joined to a team for g\_idleMapSwitch minutes. Only has
> effect when the current map is not from the map rotation.
> default is 0 (off)

rez\_r580\_lak550\_flag\_by\_name.patch
> allows flag and unflag to work by player or admin name, moved the name
> lookup code from setlevel into it's own utility function

rez\_r590\_lak550\_flag\_cleanup.patch
> clean up the !flaglist code to be more efficient

rez\_r600\_lak550\_bleeding\_spree\_fixes.patch
> fix bleeding spree to work for aliens (mostly white space changes)


> -- final touch ups --


rez\_z800\_lak550\_final\_touches.patch
> Add /mark and /teamstatus to !help command list

rez\_z901\_lak550\_branding.patch
> QVM release versioning

}}}```