#summary Rezyn's QVM featuret
Since cQvm is based off of rezyn's qvm, all of his features are included in this. To ease documentation, here is his list of featuersRezyn's QVM 1.1        - README -          June 4, 2009

Tremulous game enhancements and toys for Lakitu7's QVM v 5.5

==== Links

Rezyn QVM 1.1:
     http://mysite.verizon.net/johne/rezynqvm.html
Lakitu7's QVM 5.5:
     http://projects.mercenariesguild.net/projects/lakitu7-qvm
Tremulous dedicated servers compatible with these QVMs:
     http://tjw.org/tremulous/
     http://releases.mercenariesguild.net/tremded/


==== Features

General features:

 * End of map intermission map voting to allow players to
   select the next map.
   g_mapRotationVote Time in seconds to allow for choosing
                     the map during intermission
                     default 15
   g_readyPercent    Percent of players that need to be ready to
                     speed up moving past intermission scoreboard
                     default 0 (feature off)
   maprotation.cfg example vote section:
     *VOTE* { map1  map2  map3 }

 * Welcome messages
   g_welcomeMsg      Message to display when players connect
                     default ""
   g_welcomeMsgTime  Time to display the message in seconds
                     default 0 (feature off)

 * Killer health points, see health of attacker when you die.
   g_killerHP        default 0 (feature off)

 * /teamstatus to tell your team the condition of team base.
   g_teamStatus      time in seconds between uses of /teamstatus
                     default 0 (feature off)

 * Custom votes by cvars g_customVote1 through g_customVote8

   format: "name,message,command[,percent]"
     name     name to use with /callvote
     message  message displayed on screen
     command  commands to run when vote passes (allows semicolons)
     percent  percent of votes needed to pass (optional)

   g_customVotePercent   default vote percent needed to pass
     

 * Timelimit extend votes
   g_extendVotesPercent  percent of votes needed to pass
                         default 74
   g_extendVotesCount    number times an extend may be called
                         default 2
   g_extendVotesTime     number of minutes to extend timelimit
                         default 10

 * Layout votes to switch to a map layout

 * Popular map group
   g_popularMaps             space separated list of maps
   g_popularMapsVotePercent  percent needed to pass for these maps

   all other maps will use g_mapVotesPercent.

 * Admit defeat vote limitations
   admit defeat votes can be limited to after a set time using
   g_defeatVoteMinTime, value is in seconds, default is 60

 * Team votes or team kick votes can be disabled by g_allowVote
   g_allowVote       2 = disable team votes
                     3 = disable team kick votes

 * Chat channels and !seen.
   Chat channels work like irc:
     /join # <password>  join channel with optional password
     /part #             leave channel
     /0 /1 ... /8 /9     talk in a joined channel
   (D) !seen         find last time player was on server
   g_chat            controls name of the chat.dat file used to
                     store player's joined channels connect time

 * Karma, tries to track how a player contributes to their team.
   Persists between visits of registered players.
   g_karma   1 = on
             2 = on + auto register players with GUID
             default 0 (feature off)

 * Disallow building to players that have not set a name.
   g_newbieNoBuild   Disallow building and print a message to player
                     default 0 (feature off)
   g_newbieNoBuildMessage  message to tell players
                           default message explains how to set a name

 * GUID and ip format verification

 * Control how many connections can be made from the same IP
   g_maxGhosts       number of clients that can connect
                     default 0 (feature off)

 * Idle server map changing
   g_idleMapSwitch can be set to reduce the timelimit to expire in
   5 minutes when the following conditions occur:
     - no player joined to a team for g_idleMapSwitch minutes
     - current map was not started from the map rotation
   default is 0, off. this feature is intended to return a server to
   the map rotation if a custom map was voted and all the players left.


Admin features:

 * (A) !adminlog to show recent admin activity and votes.

 * (t) !tklog to show recent teamkills.

 * multi character admin flags, no more cryptic flags to set.

 * Admin flags can be changed per player in-game
   (f) !flag         give or deny an admin a flag
   (f) !unflag       clear (reset) an admin's flag to default
   (f) !flaglist     list all flags understood by the QVM
   (I) !immunity     make an admin immune from ip bans
   (J) !suspendban   suspend a ban for a period of time

   ( console can change admin level flags by using !flag *NN
    where NN is the admin level to adjust )

 * (d) !denyweapon to deny a player from using a specific
   class or weapon.

 * Admin chat warning when a player attempts to decon a
   protected buildable.

 * (?) !demo to mute admin chat and warnings, to hide admin
   information when recording a demo.

 * silent !specme for admins with !kick

 * Negative admin levels can now be saved between maps.
   '!listadmins 1 -1' will also list admins with
   level -1 or lower.

 * !register arguments and password.
   allows !register <level> <password>:
     level    admin level desired
     password optional password, if that level requires it.
   g_adminRegisterLevel      highest level register will accept
                             without a password.
                             default 1
   g_adminRegisterAdminLevel highest level allowed with a password.
                             default 0 (feature off)
   g_adminRegisterAdminPass  password for above
                             default "" (feature off)
   !register 0 will allow level 1 players to unregister their name.

 * (G) !expire to unregister level 1 players not seen on the
   server in g_adminExpireTime days.
   g_adminExpireTime     number of days to consider a player's
                         last connection time expired.
                         default 0 (feature off)

 * (]) !practice allows setting text, players with that text in
   their name can join any team regardless of balance.

 * Auto kick for bleeding and auto ban for repeat kicks.
   g_bleedingSpreeKick   kick a player that goes 20 percent over
                         the value of g_bleedingSpree.
                         default 0 (feature off)
   g_adminBanRepeatKicks value is in hours, a time within which if
                         the same player is kicked twice the
                         original kick will become a longer ban
                         default 0 (feature off)
   g_autoRevert          when a player is kicked or banned,
                         automatically revert buildables they
                         recently teamkilled or deconstructed.
                         value is maximum items to revert
                         default 0 (feature off)

 * !pause changes.
   Adds !unpause, instead of using !pause as a toggle.
   Individual players can be paused; or all players with '*',
   then a player can be unpaused to repair damage from
   a griefer.
   !pause has a 3 minute timeout in case admin is disconnected.

 * (x) !slap to unstick or abuse players

 * (X) !drop to disconnect a player without kick or ban

 * (q) !bubbles to draw attention to a player.

 * (h) !bring to go to the location of a player or spectator.


Gameplay altering features:

 * Dynamic build points based on player count of both teams.
   g_dynamicBuildPoints  points to add for each player on a team
                         default 0 (feature off)
   note: build points do not decrease when players leave a team

 * Build point recovery, build points of enemy-killed structures
   return slowly over time.
   g_buildPointsRecoverRate  points recovered per minute
                             default 0 (feature off)
   The build point recovery rate is effected by the stage of
   the team. Higher stages result in a slower recovery rate.
   Credits: Idea for build point recovery taken from the
            Mercenaries Guild development server (mgdev).

 * g_retribution now scales retribution proportionately
   to every player that inflicts friendly fire damage.

 * Credits overflow onto teammates.
   g_creditOverflow  1 = distribute evenly
                     2 = give to higher ranked players first
                     default 0 (feature off)

 * Marked deconstruction mode 2. Use /mark or reload to toggle
   marking a buildable for deconstruction, while allowing
   normal deconstruction behavior.
   g_markDeconstruct  2 = allow /mark and reload to toggle marking
                      1 = normal marked Deconstruction
                      default 0 (feature off)

 * Killing, feeding, and bleeding sprees.
   g_killingSpree    reward killer of a player that is on a roll,
                     value is kills per minute.
                     default 0 (feature off)
   g_bleedingSpree   base punishes players that hurt teammates/base,
                     value is multiplied by 100 to determine
                     bleeding health points per minute.
                     default 0 (feature off)
   g_feedingSpree    retard spawn rate for those that feed,
                     value is feeds per minute (per /mystats).
                     default 0 (feature off)
   (O) !outlaw       control or query player's bleeding spree value.

 * Free credits mode.
   g_freeCredits     Give players full credits after each death.
                     A value higher than 1 counts down each map, and
                     turns off when it hits 1.
                     default 0 (feature off)

 * g_mods to change basic gameplay characteristics.

   All default to 0 (feature off).
    Unless noted, cvar value is in percent of normal; a value
    of 100 will offer no change as it is 100 percent of normal,
    50 would be half and 200 would be double.

   g_modBuildableHealth  Buildable health
   g_modBuildableSpeed   Buildable fire rate
   g_modBuildableCount   Number of OMs/RCs allowed
                         0 = normal, 2 or more is max # of OMs/RCs
   g_modHumanStamina     Human stamina
   g_modHumanHealth      Human health
   g_modAlienHealth      Alien health
   g_modAlienRegenRange  Alien health regen is slower outside base
                         0 = normal, 1 = enable
   g_modHumanRate        Human fire rate
   g_modAlienRate        Alien fire rate
   g_modWeaponAmmo       Weapon ammo per clip
   g_modWeaponReload     Weapon reload time
   g_modTurretAngle      Allow high turret build angles
                         0 = normal, 1 = enable
   g_modStage3Strength   Alter stage 3 buildable ( hives and teslas )
   g_modMainStrength     Damage/range modifier for Reactor and Overmind

 * Vampire sudden death (VSD).
   g_vampireDeathTime  start of VSD time, in minutes.
                       default 0 (feature off)
   g_vampireDeath      VSD is active.
   g_vampireDeathInfo  text to include in CP messages
                       default directs them to !info vampire
   example !info vampire info-vampire.txt:
    ---- cut paste ---
^6Vampire Sudden Death^7, explained:
^2 * Both team bases self destruct
^2 * Player health slowly decreases
^2 * Damage to enemy goes to attacker as gained health
^2 * Damage to teammates gives them your health
^2 * Humans regain free ammo over time
^2 * No medkit or alien health regeneration
    ---- cut paste ---


==== List of all flags in the QVM (per !flaglist)

Ability flags:
  ACTIVITY             inactivity rules do not apply
  ADMINCHAT            can see and use admin chat
  ALLFLAGS             has all flags and can use any command
  BANIMMUNITY          immune from IP bans
  CANPERMBAN           can permanently ban players
  DBUILDER             permanent designated builder
  FORCETEAMCHANGE      team balance rules do not apply
  INCOGNITO            does not show as admin in !listplayers
  IMMUNITY             cannot be vote kicked or muted
  IMMUTABLE            admin commands cannot be used on them
  NOCENSORFLOOD        no flood protection
  NOVOTELIMIT          vote limitations do not apply
  SEESFULLLISTPLAYERS  sees all info in !listplayers
  SPECALLCHAT          can see team chat as spectator
  STEALTH              uses admin stealth
  TEAMCHANGEFREE       keeps credits on team switch
  TEAMCHATCMD          can run commands from team chat
  UNACCOUNTABLE        does not need to specify reason for kick/ban
Command flags:
  ban                  adjustban ban unban
  adminlog             adminlog
  admintest            admintest
  denybuild            allowbuild denybuild
  denyweapon           allowweapon denyweapon
  allready             allready
  bring                bring
  bubble               bubble
  buildlog             buildlog
  cancelvote           cancelvote
  cp                   cp
  demo                 demo
  designate            designate undesignate
  devmap               devmap
  drop                 drop
  expire               expire
  flag                 flag flaglist unflag
  help                 help
  info                 info
  immunity             immunity
  kick                 kick
  l0                   L0
  l1                   L1
  layoutsave           layoutsave
  listadmins           listadmins
  listlayouts          listlayouts
  listplayers          listplayers
  listmaps             listmaps
  lock                 lock unlock
  map                  map
  maplog               maplog
  mute                 mute unmute
  namelog              namelog
  nextmap              nextmap
  outlaw               outlaw
  passvote             passvote
  pause                pause unpause
  practice             practice
  putteam              putteam
  readconfig           readconfig
  register             register
  rename               rename
  restart              restart
  revert               revert
  rotation             rotation
  seen                 seen
  setlevel             setlevel
  showbans             showbans
  slap                 slap
  spec999              spec999
  specme               specme
  subnetban            subnetban
  suspendban           suspendban
  time                 time
  tklog                tklog
  warn                 warn
!flaglist: listed 18 abilities and 56 command flags


==== Building the QVM from source

These are the steps to build the QVM from source:

 svn checkout -r 966 svn://svn.icculus.org/tremulous/trunk
 cd trunk
 cat Lakitu7_Tremulous_game.qvm_5.5.diff | patch -p0
 cat Rezyn_game_QVM_1_1_0.patch | patch -p0
 make

After a successful build, the qvm is located in:
 trunk/build/release-{OS-arch}/base/vm/game.qvm

make will also build a tremded compatible with the QVM.


}}
```