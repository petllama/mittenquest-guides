# MittenQuest Guides for Polestar (unofficial)

The free World of Warcraft: Forever leveling guides of
[MittenQuest](https://github.com/rneuwi/MittenQuest) (levels 1 to 60, both
factions), converted to the guide format of
[Polestar](https://github.com/fitzforge/polestar).

This is a **community addon for Polestar**. It is **not made, endorsed or
supported by MittenQuest's author or by Polestar**. Report problems with it
here, not to either of them.

## What's in it

26 guides, MittenQuest's whole 1-60 route, in Polestar's guide menu under
Community guides. A race start route leads into one shared route per faction;
each guide hands over to the next with `next`, as in the original.

| Faction | Start routes (by race) | Shared route |
|---|---|---|
| Alliance | 1-20 Human (Elwynn), Dwarf/Gnome (Dun Morogh), Night Elf (Teldrassil) | 19-23, 23-27, 27-31, 31-35, 35-40, 40-44, 44-48, 48-52, 52-56, 56-60 |
| Horde | 1-13 Orc/Troll (Durotar), Tauren (Mulgore), 1-14 Undead (Tirisfal) | 12-19, 19-25, 25-29, 29-34, 34-38, 38-42, 42-46, 46-50, 50-54, 54-60 |

MittenQuest has no Skyborne start route; Skyborne characters can pick up the
shared route.

## Install

1. Install **Polestar 0.2.6 or newer** first.
2. Download `PolestarPack_MittenQuest-<version>.zip` from this project's
   [releases](https://github.com/petllama/mittenquest-guides/releases) and unzip
   it into `Interface/AddOns/`, next to `Polestar`.
3. Restart the game. The guides show in Polestar's guide menu
   (`/polestar guides`) under Community guides; Options › Community guides
   (`/polestar packs`) turns the addon on or off.

You don't need MittenQuest itself, and it's best not to run both guide addons
at once.

## How it differs from the original

The conversion is automatic. The route, the quests and the step notes are
MittenQuest's; how they run is Polestar's. Both are built on the same open
quest data (QuestieDB), so every quest, NPC, item and object keeps its id.
Known differences:

- **Objectives** ("complete" steps) are the quest's own objectives (kill,
  loot, use an object), at MittenQuest's spot unless it is far from every
  spawn Polestar knows; MittenQuest's mob list and drop chance are the step's
  tip.
- **Optional quests** (group quests and side chains) work as in the original:
  their objectives and turn-in show only while the quest is in your log, and
  an optional follow-up shows only once its prerequisite is turned in. The
  accept itself waits for you: take it or press Skip.
- **Elite-only objectives** are optional, with a "group up" note.
- **Class training** steps are Polestar's "visit your class trainer" goal for
  your class (the nearest trainer, not always the town MittenQuest names).
- **Dungeon steps** list the carried dungeon quests; they show while you have
  one of them and finish when they are done (or skipped).
- **Five quests left out:** the Human start route offers five Westfall quests
  (The State of the Mines, Murloc Gills, Moonbrook Espionage and two Destruction
  in Deadmines) that Polestar's quest data marks as not available to Humans.
- The expected-level pace display and route tuning log are MittenQuest
  features and are not part of this.

[`reports/`](reports) lists every step the conversion dropped
(`conversion.json`) and every automatic fix applied from Polestar's checks
(`lint-fixes.json`).

## Licence and attribution

The guides are an adaptation of MittenQuest's guides:

- **Source:** [rneuwi/MittenQuest](https://github.com/rneuwi/MittenQuest), the
  files `Guides/*/*.lua`, at the commit named in [SOURCE.md](SOURCE.md).
  MittenQuest's route is generated from [QuestieDB](https://github.com/Questie/QuestieDB)'s
  Forever data (Questie, GPL-3.0); thanks to the MittenQuest, Questie and
  QuestieDB authors.
- **Licence of the source:** GNU General Public License v3.0.
- **Changes:** converted to Polestar's `.guide` format: steps and conditions
  rewritten, quest objectives, NPCs and items resolved against Polestar's
  reference data. MittenQuest's addon code isn't included.

This adaptation is licensed under the same **GPL-3.0** (full text in
[LICENSE](LICENSE)). The `.guide` files in this repository are its source.

The built addon also contains facts from Polestar's reference data (quest,
NPC and map data), which Polestar's compiler places in it. Polestar's
[licence exception](https://github.com/fitzforge/polestar/blob/main/LICENSE-EXCEPTION.md)
lets a compiled pack carry them under the pack's own terms.

"MittenQuest" names the source of the guides; no trademark rights are claimed.

## Building it

The pack is built from the `.guide` files in `guides/` with Polestar's own
tools (Node 24+, Lua 5.1, a Polestar clone with `npm link`, its reference data
built with `polestar data build` and `polestar travel build`):

```sh
polestar lint       # check the guides against the game's data
polestar playtest   # play every guide to the end in the real addon
polestar pack       # write the release zip to dist/
```

The `.guide` files are generated. Fix a problem in a guide by opening an issue
here: hand edits are lost at the next conversion from a newer MittenQuest
source.
