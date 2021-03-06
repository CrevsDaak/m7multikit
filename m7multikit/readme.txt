                             Baldur's Gate II
                        Multiclass Multikit Builder
                              Version 0.28

		Table of Contents
		~~~~~~~~~~~~~~~~~
I.   About
II.  Compatibility
III. Installation
IV.  Technical
V.   Known Bugs
VI.  Changelog


		Section I. About
		~~~~~~~~~~~~~~~~
Ever wanted to play an Anti-Paladin/Necromancer/Assassin? What about a Kensai/
Transmuter/Bounty-Hunter? Berserker/Priest of Talos? Or maybe even a Barbarian/
Wildmage/Adventurer?

Well, now you can. This mod creates a multikit from the kits you select during
installation (or by editing the tp2 file, but that isn't normally recommended).
You must them apply the kit with the auto-generated script. There are some limitations,
yes --see the bugs section-- but everything I tried works.

You gain abilities of a class when you gain levels in that class, kit item
restrictions are obbeyed and the mod even attempts to combine kit limitations
on skill levels. Wild Magic works too, if you want that.

Note: a multikitted true-class mage will *not* gain an extra spell per level as
normal kitted multiclasses do -- I fixed *that*. :-)


		Section III. Compatibility
		~~~~~~~~~~~~~~~~~~~~~~~~~~
This mod should be installed after any mods that add new kits or that change kit
abilities. By doing this, you ensure that all kits you have installed can be
used to make multikits, as well as ensuring that their abilities match.

*Currently*, this mod is incompatible with Refinements.


		Section III. Installation
		~~~~~~~~~~~~~~~~~~~~~~~~~
BGII is required. ToB is required for many components, optional for the others.
I have tested this with a hefty collection of mods stacked on top of each other,
so you should be safe in most scenarios.

Unzip the main ZIP file into your BGII main directory. This is normally:
        C:\Program Files\Black Isle\BGII - SoA\

This mod doesn't contain the executable required to be installed. You can get a
copy at https://github.com/WeiDUorg/weidu/releases.
After you've downloaded that, rename "weidu.exe" into "setup-m7multikit.exe" and
run (click on) that.

First, pick your favorite language. Currently available: 
  English 

Then choose which components you would like to install. You may always
uninstall them later by re-running "setup-m7multikit.exe".

The first component allows you to create multikits. It can be installed as many
times as you want, but it can't be uninstalled. The created multikits will be
saved to a tp2 file.

The second component allows you to delete the multikits you created with the
first component. It also can be installed as many times as you want and it also
can't be uninstalled. Each multikit you remove using this method will first be
uninstalled as if you had manually unistalled it first.

After you create any multikits you want, the setup will automatically launch
the multikit installer, which allows you to actually install the multikits to
the game. You can install or uninstall each multikit separately.

As a rule, you do *not* need to start a new game to take advantage of anything
you installed. You just need to select the generated AI script for the character
you want, turn on party AI, apply the kit with 'K' and revert to whatever other
script you fancy, and even disabling party AI if you want. To disable the kit,
select the generated AI script for the character you want, turn on party AI and
disable the kit with 'N'. You can revert to any other script you like, or turn the
party AI off altogether.


		Section IV. Technical
		~~~~~~~~~~~~~~~~~~~~~
This mod works as follows:

1) It creates a kit for the multiclass of your choice. This is a kit for *the*
*multiclass* -- for example, FIGHTER_MAGE_THIEF. This accomplishes a tiny thing:
the description and title are correctly displayed for the multikit. But the clab
file is left unused (since you gain levels in the base classes, not on the
multiclass), hence only a dummy clab is used here.

2) It parses the clab files for each kit and generates new spell effects that
will be used on level up. These spell effects are conditionally applied based
on a preset value added to specific.ids, and are then added to the clabs for the
*base* *classes* of the multikit.

3) When you level up, you gain the conditionally applied abilities from the base
class in which you leveled up. This includes the conditionally applied effects
that were created above.

4) An AI script is created which is used to apply the kit to the character.

The mod tp2 and an included tpp have extensive comments giving examples of how
you can use it on your own mod, including how you can make a predefined multikit
instead of having to go through all the choices.

The 'multikits.tp2' file is dynamically expanded as you create multikits. You
can use this file to install multikits, or grab portions of it to include in a
mod. In either case, this tp2 uses all files in the m7multikit directory tree,
and you should include the entire tree in your mod. Just be sure to set the
correct paths, and copy the ALWAYS statement, and you are set.


		Section V. Known Bugs
		~~~~~~~~~~~~~~~~~~~~~
You can't start the game with a multikitted multiclass. This means that skill
points for thieves and barbarian hit points will probably be incorrect.

Removing the kit is slow under the new method. Also, some effect-heavy multikits
may cause an in-game slow down compared to the old method.

Some items, such as the Soul Reaver from Tactics, use special 'hacks' to let
only anti-paladins use them. An antipaladin multikit will not be able to use the
Soul Reaver because of this.

There are probably cases when the generated weapprof.2da column for a given
multikit does not make much sense. I'd appreciate knowing about these cases.

If you have TobEx/are playing on an Enhanced Edition game, the Hit Points will
always be the ones of the base Multi-class due to an engine limitation.

Compatibility with GemRB is not yet implemented and completely untested. However,
you're encouraged to try and report back any issue(s).

		Section VI. Changelog
		~~~~~~~~~~~~~~~~~~~~~
Version 0.28:
        * Multikits can now be chosen at character creation in EE.
        * No longer lists fake Cleric kits when building Multikits in EE.
        * Special thanks to aquadrizzt for letting me use parts of
          his qdmulti library in this mod.

Version 0.27.11:
        * Fixed the bug introduced in the previous version that prevented
          the user from installing any multikits. Althought, yet another
          bug might have been created in the process. I apologize in advance.

Version 0.27.10:
        * Finally fixed the bug with the HLAs table, but introduced a new one.

Version 0.27.9:
        * Fixed a bug that prevented multikits from getting their HLAs table.

Version 0.27.8:
        * Numerous bugs for EE were fixed.
        * Non-Generalist Mages now get their extra Spellslot per level
          as they should.
        * No longer fails to install due to an incorrect number of
          columns being appended to a clab file.
        * Custom title selection enabled!
        * Updated prompt about the Kit's internal name to warn the user of
          using numbers as the first character of the name.

Version 0.27.7:
        * No longer gives false warnings with Mage/Thief multikits.
        * Some multikits no longer fail to install in EE due to a mistake in the code.

Version 0.27.6:
        * No longer fails to install Mage multikits.
        * Wild Mage's XP deduction now correctly calculated (it works now).

Version 0.27.5:
        * Installation no longer fails due to a syntax error because
          I'm bad with git.

Version 0.27.4:
        * Fixed a bug that caused Wild Mages to get the incorrect amount
          of XP drained to compensate the special Wild Mage spells' XP
	  reward, which caused a great XP loss and if the character
	  had less than 10,000 XP it would make them reach level 40 on
	  every class.
	* Updated to WeiDU 240.
	* Added SoD compatibility.

Version 0.27.3:
        * Licensed under the MIT License as per FlameWing's wishes
          (which I consider to be a really good idea actually).
        * Updated TobEx to 0026 Beta, and added a small fix so it doesn't
          crash on Wine'd BG2:ToB installs in OS X.

Version 0.27.2:
	* No longer fails to install on Enhanced Editions games if a non-Thief
          Multi-class combination is chosen.

Version 0.27.1:
	* No longer fails to install (an ACTION_IF was being used inside a
          patch_list).

Version 0.27:
	* Avoid chunking on missing HLAs referenced in the lu*.2da table.
	* Added base for avoiding normally unelectable Kits.

Version 0.26:
	* Fixed a bug that caused a warning and made it impossible to use
	  Multikit-specific values for some .2da files on Enhanced Edition games.
	* Fixed a bug that made impossible to disable the Multikit on Enhanced
	  Edition games.
	* Changed hotkey to remove Multikit to 'N' and documented that.

Version 0.25:
	* Added support for Enhanced Edition games.
	* Fixed a bug that caused all Multikits to use the same specific.ids
	  value.

Version 0.24:
	* Error messages from v0.23 moved to tra.
	* Improved handling of designation numbers for generated kits.
	* All components depend on the core multikit component (this includes
	  generated multikits, but not the core component itself). If an older
	  multikits.tp2 file is found, it will be upgraded to include these new
	  dependencies.
	* Fixed several parsing errors and omissions when adding, when reading
	  or when deleting multikits to/from 'multikits.tp2'.
	* Includes redistributable TobEx Beta 0021. Wild mage spells known now
	  use TobEx extended learn spell opcode to not give XP.
	* Fixed errors with: mage specialists; original priest kits; bounty
	  hunter kit; wizard slayer kit; totemic druid kit; beast master kit;
	  undead hunter kit.
	* Fixed errors with true classes not being correctly named.
	* Improved weapon proficiency table building -- a kit will only reduce
	  the maximum mumber of stars in a proficiency if the kit forbids a
	  weapon which the base class did not; otherwise, the best value so far
	  (chosen from the selected kits and the base multiclass).

Version 0.23:
        * Fixed version number.
        * Updated to WeiDU 230.
        * Using TRY/MATCH to work around invalid files.

Version 0.22:
        * Fixed handling of 0-byte files.

Version 0.21:
        * Getting previous version to actually work.

Version 0.20:
        * Somehow, the new algorithm for maximum # of stars hadn't made the cut;
          it now has been included.
        * Added a multikit remover, with a pure WeiDU file reader/rudimentary
          parser. The old multikits.tp2 file, if you keep it, will automagically
          be upgraded to include a forced designation which (hopefully) will be
          correct. The multikits will be uninstalled before being deleted.
        * Brand new HLA table editor allows merging of kit HLA tables and also
          removal of excess HLAs.
        * Spells from the wrong mage schools are now permanently removed when
          the multikit is applied.

Version 0.16:
        * Fixed backup collision between main tp2 and kit tp2.

Version 0.15:
        * Refactored multikit building into creation and installation, which
          occur at separate stages. Multikits will be saved into a separate tp2,
          which is invoked at the end allowing you to selectively install from
          the multikits you have created.
        * New algorithm for determining maximum # of stars for the multikit.
        * The multikit creator will 'explode' the applied spell effects into
          eff files, which are conditionally applied. This allows proper removal
          of these effects when the kit is removed. Also, a hack involving base
          kit cycling allows removal of kit-granted innate abilities. Both of
          these some with some in-game performance hit; the old (buggy) method
          is still available by editing the tp2 file.
        * The 10,000 XP granted by learning Wild Magic spells is now removed.

Version 0.12:
        * Adding the kit or levelling up were causing combat music to play and
          would disable saving as if you were in combat; this was due to a
          misflagging of the effect files.
        * Correct script name will be displayed once the multikit is created.

Version 0.11:
        * Fixed unusability bug for kits with identical usability (e.g., true
          classes).
        * Fixed array indexing bug.

Version 0.10:
        * Initial public release.
