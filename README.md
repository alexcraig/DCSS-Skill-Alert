# DCSS-Skill-Alert
A Lua sript for Dungeon Crawl Stone Soup init/rc files which allows the player to be notified when a skill reaches a trigger level.

# Installation
To install, copy the entire lua code block contained in "skill_alert.txt" into your DCSS init/rc file.

If your init/rc file already includes a definition of the `ready()` function, omit the `ready()` function definition from the block contained in skill_alert.txt, and instead add a call to `check_skill_alerts()` into your existing `ready()` function definition.

# Usage
To use the script a macro must be bound to the 'set_skill_alert()' function.

To make a macro binding the function to a key, use Ctrl-d followed by m to define a macro, then enter the key you'd like to bind to the macro, and finally enter a target name of '===set_skill_alert'.

Upon activating the 'set_skill_alert' macro, the list of currently watched skills will be printed to the crawl message log. For example:

`Skill alert currently watching: Short Blades[2.1|4], Spellcasting[2.3|3], Charms[0|3]`

Watched skills are listed in the format: `<Skill Name>[<Current Skill Level>|<Alert Trigger Level>]`

The script then prompts for a skill name to be watched / unwatched. The entered skill name is matched using a case insensitive substring search, so shorthands can be used at this step (for example, entering "evo" will match against the "Evokables" skill). Entering an empty string or cancelling the prompt will terminate the script without modifying the list of watched skills (useful if you just want to check the currently watched skills). 

If the entered skill name is a skill which is currently being watched, then the skill is removed from the watched list, and the list of watched skills is re-printed. If the entered skill name is not currently being watched, the script will prompt for a skill level at which an alert should be triggered.

When a watched skill reaches the set trigger level, a message will be printed to the message log in the following format:

`Watched skill <Skill Name> reached level <Current Skill Level>`

The script will force a "more" prompt, and then open the skill training screen. The script does not disable training of the watched skill, this is left for the player's judgement.

# Known Issues / Limitations

- The list of watched skills currently persists between characters (i.e. death does not clear the list of skill alerts)
- The skill alert script has only been tested with the 0.18 WebTiles version of DCSS.
