
[<p align=center>]() [Home](readme.md#pure-speed-pure-skill-pure-fps) | [Setup](setup.md) | [How To Play](howtoplay.md) | [Impulse Commands](impulse.md) | [Champions](champions.md) | [Advanced Movement](movement.md) | [Weapons](weapons.md) | [Items](items.md) | [Multiplayer](multiplayer.md) | [New Maps](maps.md) | [Custom Maps](custommaps.md) | [Change Log](changelog.md)


# <p align=center>CHANGE LOG</p>
[Version 11](#version-11)<br>
[Version 10](#version-101)<br>
[Version 9](#version-9)<br>
[Version 8](#version-8)<br>
[Version 7](#version-71)<br>
[Version 6](#version-6)<br>
[Version 5](#version-5)<br>
[Version 4](#version-4)<br>
[Version 3](#version-3)<br>
[Version 2](#version-2)<br>
[Version 1](#version-1)<br>

---
## Version 11

#### Additions

- New Map: Insomnia. Supports Deathmatch.

- Added ammo types Bullets, Bolts, and Slugs. Not currently implemented, for now they spawn Spikes, Rockets, and Cells respectively.

- Added qcc_weapon_tribolt. Not currently implemented, for now spawns a grenade launcher.

#### Bug Fixes

- Rerendered Duke "TRD" line from stereo to audio. Should play properly now.

- Fixed broken precache of Duke "bug" line. Should play now.

---
## Version 10.1

#### Bug Fixes

- Big John can exit the water now. The fix required making his hitbox slightly shorter, matching the same height as Scalebearer and Sorlag. Removed water checks for slow champs in the QCC Pre/Post Think functions since they were meant to try to fix this issue.

- Added a condition for the Big John bots that will hopefully fix their ability useage.

- Big John now only calls out his own name when you swap to him at the start of a match.

- Cleaned up Big John Big Gun view model animation.

---
## Version 10
#### Additions

- Added Keel.

- Added Big John.

- New Map: Crucible. Supports Deathmatch and Horde Mode.

- New Impulse Command: Cycle Previous Champion.

- Bouncepads!

- Special Health. This item gives 25 health with the added ability to overstack. Special Health first appeared in Quake Champions on the map Crucible, in the location the Power Up used to be at before it was moved to the center of the map.

- `qcc_prop_dynamic`.

- FGD updated to include new entity classes.

- Info Intermission now takes optional `target` and `targetname` fields, which can be used to aim the camera at a target and update the camera's position respectively.

- Cthon now has a `Don't freeze on pain` spawnflag. Dimension of the Machine reworked Cthon to make him killable with the Lightning Gun, but it was also a heavily scripted and conditional fight (by Quake's standards) where after every third of his health was lost Cthon would freeze and sink into the lava via an elevator, and would only rise again when triggered by a key collection. Now if you set both his `Killable` and `Don't freeze on pain` spawnflags Cthon can just be placed in a level and murdered (still only to the Lightning Gun).

- Trigger Change Level now has a `changelevel_use` function, allowing remote level changing.

#### Changes

- Major codebase reorganization and revision. Hopefully this will allow players to be a bit more responsive (if function order even *really* matters, idk).

- Doom Slayer now only makes pain sounds when below 50 health.

- Duke Nukem's Devastator now deals full damage to Shamblers.

- Multi-grenades will now always shower mini-grenades. Previously they would only spawn mini-grenades after a timer, and would do a simple grenade explosion on contact with a living entity. Currently used by the Boss Ogre and Keel.

- Multi-rockets no longer deal a random amount of bonus damage, instead doing a flat rate per rocket. They're not accessible by the player, but they could be added to an enemy in the future.

- Self damage reduction is now controlled by `.qccSelfDamage`, a float multiplier. When not set by an entity it defaults to 0.5. Currently used by Ranger and Keel.

- DoE Dragon now has the rocket resistance flag instead of classname checks in damage functions.

- QC style Quad and Pentagram powerup now despawns if not picked up within 30 seconds.

- Horde Mode Items no longer spawn Hourglasses. Instead they have a 1 in 6 chance of spawning a Special Health.

- `func_spawn` has been reworked to be more KISS compliant.

- SoA Gremlins limited to 25 clones in Horde Mode.

- Goroth's explosive attacks should no longer blow out your speakers.

- Increased Info Intermission camera count to 10.

- Cthon, Fiend, DoE Guardian (Morph) and DoE Hephaestus (lavaman) code cleaned up.

#### Bug Fixes

- DoE Plasma Gun lightning bug fixed. Even though the Plasma Gun isn't useable for the player, the Dragon's projectile attack uses the same code. Don't know if this will make it harder or easier.

- Fixed dropped powerup from killed Quad / Pent bearer not despawning after a short period.

- DoE Guardian (Morph) should no longer be invisible in Horde Mode.

- DoE Guardian should no longer perpetually scream or glow after dying.

- Goroth and Volkerh's FGD definitions now use the correct size.

- Dropped power ups should now correctly give the remaining time left while also disappearing from the map. No more powerup dupes!

- Protection should no longer gimp rocket jumps.

#### Known Issues

- Keel and Big John head gibs don't apply the proper skin.

- First power up doesn't print the "Incoming" / "Spawned" messages.

- Crucible: Bots have difficulty navigating bounce pads and ledges and sometimes get stuck in certain areas.

- Crucible: Bots in Horde mode have issues recognizing locked doors.

[Top](#change-log)<br>


---
## Version 9
#### Additions

- Added Slash.

- Added Anarki.

- Added Observer Class; recommend "bind o impulse 29".

- Heavily reworked source ID1 and QCC source file structure and cleaned up code.

- Player class cleaned up. Now performs checks for custom player animations.

- Added custom attack functionality. Should help in the future for BJ, Strogg, the Champion, and others.

- Added QCC Flag QCC_FL_INFIGHT, to more cleanly allow monsters of the same class to infight.

- Added messages.fgd include from Dimension of the Machine FGD pack.

- Added entity model definitions to qcc.fgd.

#### Changes

- Death Knight now has a unique Flame Strike animation.

- Scalebearer Bull Rush should stop if colliding into an enemy does not kill it.

- Grenades now deal direct damage the same way Rockets do.

- Removed specific checks for "monster_army" and "monster_armagon" in T_Damage's in-fighting section and replaced with .qcc_flags check for new QCC_FL_INFIGHT flag.

- Cleaned up Grunt code. Added infighting QCC Flag to `monster_army()` spawn function.

- Cleaned up Armagon code. Added infighting QCC Flag to `monster_armagon()` spawn function.

- Cleaned up Shambler code. Added rocket resistance and lightning resistance QCC Flags to `monster_shambler()` spawn function.

#### Bug Fixes

- Champion ability impulse should no longer buffer, providing more reliable ability useage.

- Champion state abilities (Ghost Walk, Berserk, Bull Rush) now check for the DEAD_DYING deadflag. Hopefully this will fix the frozen champion bug.

- Champion ability cooldown is started if player dies mid-ability.

- Corpse models in Dimension of the Machine maps should now display the correct animation frame.

- Added a check to hopefully avoid accidentally using abilities on respawn.

- Sorlag Air Control passive should only increase speed if already moving.

- Sorlag Acid Spit should no longer get stuck unmoving in the air.

- Intruder's Fast Fire Totem now doubles attack speed for the Nailgun and Lightning Gun.

- Dimension of the Machine Runes should now spawn appropriately. Accidentally forgot a ".bsp" extension in the map checks for them.

- Dimension of the Machine Runes can now be thrown by Intruder, just as intended John Romero intended.

- Skins should be selectable in coop and horde modes now. Previously they would auto-switch to Red Team.

- Picking up a health box while on fire or poisoned should now consume the health box even if at full health / overstacked.

- Pentagram of Protection now reduces damage by 67% instead of 33%, making it infinitely more useful.

- Changed player_run() self.walkframe check to >= 6 from == 6, just in case walkframe gets set elsewhere.

- Reworked Death Knight's Flamestrike animation calls. This combined with the above self.walkframe fix should get his animations playing properly finally.

- Implemented Shambler Lightning Arc Fix from Progs_Dump.

[Top](#change-log)<br>


---
## Version 8

#### Additions

- Added Scalebearer.

- Added Sorlag.

- Added Dissolution of Eternity support. Use xpax.bat for ease of copying over the required data.

- Added Linux shell script "xpax.sh" written by Slipseer community member plague_spreader.

- Added flag to allow Quad <-> Pentagram respawn swaps when collected (collect Quad, respawns as Pent, collect Pent, respawns as Quad).

- Horde Mode: Added 5% Horn of Conjuring, 10% Empathy Shield, 10% Power Shield, 5% Anti-Gravity Belt chances to Powerup Drop.

- Added black bearded Intruder skin.

- Added gib skins for Intruder. Gibs now correspond with current player model skin.

#### Changes

- Players now drop their possessed powerups when they die (Quad, Pentagram, and Ring only).

- Quad, Pentagram, and Ring now have 90 second delays before their first spawn in Deathmatch, then 120 seconds between respawns afterward.

- Pentagram no longer provides invulnerability; instead it reduces damage by 2/3 3rds.

- Horde Mode: Changed Pentagram drop rate from 25% to 30%. Quad drop rate lowered from 75% to 40%.

- Lightning Gun now does 13 * cell ammo when fired in the water. It's technically less damage, but still almost 2000.

- Nyx Invis time lowered to roughly 3 seconds (mistakenly set higher).

- Doom Slayer Berserk time lowered to roughly 5 seconds (mistakenly set higher).

- Doom Slayer Berserk movement speed increased to 500 UPS.

- Commander Keen's Pogo Stick is a bit easier to navigate with.

#### Bug Fixes

- Reworked Obituary cross-engine compatibility, setting appropriate .killstring, and .deathtype fields based on extension support.

[Top](#change-log)<br>

---
## Version 7.1

#### Bug Fixes

- Running out of ammo with Commander Keen should no longer throw a runaway loop.

- Gremlins shouldn't be able to steal Champion Abilities. They couldn't use them anyway, but better safe than sorry.

---
## Version 7

#### Additions

- Added Commander Keen.

- Added Scourge of Armagon support / requirement. Use xpax.bat for ease of copying over the required data.

- Added Class Speed Differences. This is the start of adding different movement options for certain champions.

- Added Armorshards. They get thrown by players on death in multiplayer, and by certain enemies.

- Abilities can now have a variable cost. This will allow for things like Keel having 3 grenades or Athena having 2 grapples. Currently only used for Commander Keen. The 20 second Dire Orb will not be making a return, sadly.

- Horde Mode now has a 33% chance to spawn hourglasses, 50% chance to spawn Health, and ~17% chance to spawn the new Light Armor.

- Added Horde condition to Hourglass pickup.

- New console background.

- Added Ruby Nyx and Trans Ally Duke skins.

- Some gibs now have multiple skins. Currently Nyx and Commander Keen.

- Weapon Wheel now supports the Railgun, Laser Cannon, and Proximity Gun (Mjolnir will be added at a future date).

- Status Bar Ranger Face replaced with "generic" Health Symbol.

- FGD updated to support Scourge of Armagon, Dimension of the Machine, and new Quake Champions Classic items.

#### Changes

- Weapons now give ammo according to current Quake Champions rules:
	* If max ammo is 25, give 10 if below 10, otherwise give 5
	* If max ammo is 150, give 100 if below 100, otherwise give 10

- Ammo Boxes now give ammo based upon current Quake Champions rules:
	* If max ammo is 25, give 5 for small and 10 for big
	* If max ammo is 150, give 25 for small and 50 for big

- Green and Yellow Armors now spawn in as Light Armors (+50). Red Armor now spawns in as Heavy Armor (+100, overstacks). Respawn times set to 30 seconds.

- Armor now absorbs a flat 67% of damage. No more varying absorption rates.

- Champion Classes now affect starting and maximum armor values.

- Champions with a special jump ability now assign it to qccJumpFunc. This avoids a huge conditional check in the Client Jump function.

- Resized and tilted all champ head gibs to be more in line with the default player gib.

- Ending music changed to Quake Main Theme.

- Ranger's Dire Orb now has Quad Glow.

- Ranger should more consistently warp inside enemies that have been Orbed. Still needs more testing.

- Nyx's Ghost Walk now prevents item pickup.

- Nyx's Ghost Walk no longer shows Quad / Pentagram glow while active.

- Cthon can now be telefragged. He is still impervious to other weapons.

- Railgun now only replaces one Rocket Launcher if there are more than 1 in a Deathmatch map.

- Ability Ready sounds will now only play for the player and not the world if the engine supports "localsound". Otherwise, fall back to previous behavior.

- Health overstack now carries over to the next map in SP and Coop.

- Refactored Bot ability use code. You probably won't notice.

#### Bug Fixes

- Champions can now be selected properly after changing maps in a server.

- Railgun will now only replace a Rocket Launcher at the start of a map.

- Locked buttons now display the correct required key. Plays locked sound again.

- Weapons in multiplayer now only trigger their targets the first time they are picked up. This was a missed line when porting over MG1 QC code. This should resolve the Cthon fight issues at the end of Dimension of the Machine and potentially any other coop weapon trigger issues.

- Horde mode used to not spawn rotten healths because of a missing else conditional. Fixed this after the rotten health->hourglass swap.

- Abilities will no longer weapon lock you when changing levels while an ability is active. Should also fix some respawn bugs, too.

- Connected players now increments, allowing coop item code to work.

[Top](#change-log)<br>

---
## Version 6

#### Additions

- Added the Intruder from DUSK. Don't tell David.

- Added Champion Select Menu for Rerelease. You activate the menu the same way as cycling through champions. Falls back on old behavior when using other engines. Unfortunately this is not feasible for skins, due to the number of impulse commands that would be required.

- Added Dimension of the Machine and Horde Mode support. Dimension of the Past supported by default. A batch file is included to assist with this.

- Added Ranger + Nyx ability telefrag messages. They don't seem to work properly yet though, I'll have to straighten that out next update.

- Shub Speaks! upon seeing a player.

- Player Gibs now have a new BodyQueue system to support the Intruder. This potentially doubles the amount of corpses in play.

- Added Railgun to Rerelease Weapon Wheel. Currently uses Lightning Gun icon.

#### Changes

- Consolidated everything into the Rerelease QC files. Every sprint, bprint, and centerprint call now has backwards compatibility with the old string formatting. A little painful to implement, but eases the development A LOT. Fewer QC files to maintain, and adds the possibility of adding language support for Rerelease in the future more easily.

- Remapped QCC impulses due to how the Rerelease Champion Menu needed to be implemented. Be sure to update your key binds!

- Nyx Ghostwalk color shift is BLUE now.

- Doom Slayer has less blood in his eyes when going Berserk.

#### Bug Fixes

- Skins now appropriately wrap through the individual champion's available skins. Ring of Shadows and Nyx's Invis now use skin 0, then set the skin back once visible again. No more endless console complaints!

- Ranger Bots should more frequently warp to their orb if a potential enemy is close enough to it (32u).

- Duke Nukem no longer has the ability to start talking underwater. Probably. If he starts talking moments before hopping into the water, he'll continue to. I'll fix that next update. Probably.

#### Known Issues
- Final boss in Dimension of the Machine seems to have scripting issues when playing in Coop. This may be a wider issue for coop. Currently works in Single Player.

- Horde Mode Lock Buttons will print the wrong key type, but still require the correct key type.

These issues are likely fixable. Will look into it next update.

[Top](#change-log)<br>

---
## Version 5

#### Additions

- Added Railgun. Multiple DM maps either had rocket launchers replaced or a railgun added. Every id1 episode has 1 railgun to find. Recommended bind: bind r impulse 109

- Added Bot Support. Bots will randomize Champion picks and skins. They will also use the new Railgun and their Abilities when they feel appropriate. They may still have some bugs, but seemed to test fine as of version 5's release.

- Added alternate skins for Death Knight.

- Ranger and Duke Nukem now have Green Skins. Doom Slayer will retain his Green Skin when on Green Team in Team Deathmatch.

#### Bug Fixes

- Kill command in multiplayer no longer crashes the game. The issue was the "set_suicide_frame" method checking for a specific player MDL. Now it just checks if the model is the Champ Gib model.

- Current Champions should no longer exit Abilities early or get stuck in them.

[Top](#change-log)<br>

---
## Version 4

#### Additions

- Added Duke Nukem

- Added Ability and Melee Weapon specific kill messages

- Shub now looks for players before going into standard idle. This allows player reactions upon "seeing" her.

#### Bug Fixes

- Skins now properly change and are maintained across deaths

- Weapon autoswaps, weapon + ammo pickups no longer switch away from active abilities

[Top](#change-log)<br>

---
## Version 3

#### Additions

- Added Doom Slayer

- Melee Weapons now produce customizable wall hit sounds and optional enemy hit sounds

- Added skin support:
	* In most engines changing teams will change skins.
	* In Rerelease, skins change based on teams only in team mode. In free for all modes, use "impulse 137". I bound it to K.
	* Currently utilized only by Ranger and Doom Slayer, but planning support for others.

#### Changes

- Changed Dire Orb speed from 500 to 620, to be roughly twice Ranger's base move speed.

#### Bug Fixes

- Fixed Wall/Double Jump Bug: in the event that a player queued up a new Champion without double jump after dying mid double jump as Nyx or Doom Slayer, they were unable to jump. Now self.qccDoubleJump gets reset to 0 on respawn.

- Fixed Ranger Dire Orb animation bug: interrupting the Dire Orb think process could cause Ranger to be unable to act. Dire Orb throw animation now utilizes standard animation function calls.

#### Known Issues

- Berserk ability tilts the view angle due to the way the red tint is acquired. I felt this was an acceptable tradeoff since this mod is intended to be QC only + re-release compatible, and color tints seem to be hardcoded to specfic scenarios.

[Top](#change-log)<br>

---
## Version 2

#### Additions

- Added Nyx

- Champion selection persists across levels (reverts to Ranger if you use the map cheat)

- Added Ability Ready notification + sound

- Added Hourglass pickup sound, no longer uses rotten health

- Changed Shub Death scene to show current champion

#### Changes

- Monsters no longer print the ability timer cooldowns, now only hourglasses and attempting to use the ability will

#### Bug Fixes

- Fixed armor reset bug - armor now only gets set on spawn in Deathmatch modes

[Top](#change-log)<br>

---
## Version 1

- First release

[Top](#change-log)<br>

---

[<p align=center>]() [Home](readme.md#pure-speed-pure-skill-pure-fps) | [Setup](setup.md) | [How To Play](howtoplay.md) | [Impulse Commands](impulse.md) | [Champions](champions.md) | [Advanced Movement](movement.md) | [Weapons](weapons.md) | [Items](items.md) | [Multiplayer](multiplayer.md) | [New Maps](maps.md) | [Custom Maps](custommaps.md) | [Change Log](changelog.md)
