# Artificer Permanent Elixirs

A small Baldur's Gate 3 patch for the [Artificer](https://www.nexusmods.com/baldursgate3/mods/1779) class mod. It makes **Experimental Elixirs permanent**.

## What it does

In the Artificer mod, Experimental Elixirs are summoned items. They disappear when you take a Long Rest, and when the Artificer who made them leaves the party.

With this patch, elixirs are made as normal items instead. They stay in your inventory until someone drinks them, so you can:

- Stockpile elixirs across Long Rests
- Hand them to any party member, or put them in camp storage
- Keep them after the Artificer leaves the party

Everything else works the same as before: how many elixirs you can make per Long Rest, using spell slots to make more, the random effects, and the upgraded elixirs at Artificer level 9.

## Requirements

- [Artificer](https://www.nexusmods.com/baldursgate3/mods/1779)

## Installation

1. Install the Artificer mod.
2. Import `Packages/ArtificerPermanentElixirs.zip` (or the `.pak`) with your mod manager, such as BG3 Mod Manager.
3. Put this mod **after** Artificer in the load order.
4. Export the load order and start the game.

Elixirs you made before installing the patch are still the old kind and will disappear on your next Long Rest. Any new elixirs will be permanent.

## How it works

The patch overrides the Artificer's five elixir spells (Healing, Swiftness, Resilience, Boldness, Flight). The original spells use `SummonInInventory`, which creates temporary summoned items. This patch replaces that with `SpawnInInventory`, which creates normal items. All other spell data is copied unchanged from the Artificer mod. The patch also updates the elixir tooltip text to say the elixirs are permanent.

## Project layout

```
ArtificerPermanentElixirs/
├── Localization/English/ArtificerPermanentElixirs.xml   # Updated tooltip text
├── Mods/ArtificerPermanentElixirs/meta.lsx              # Mod info and Artificer dependency
└── Public/ArtificerPermanentElixirs/Stats/Generated/Data/Spell_Shout.txt  # Elixir spell overrides
Packages/                                                # Built .pak and .zip
```

## Building

Requires Python 3 and [LSLib](https://github.com/Norbyte/lslib)'s `Divine.exe`.

1. Set `divine_path` in [build_config.yaml](build_config.yaml) to your `Divine.exe` location.
2. Install dependencies: `pip install -r requirements.txt`
3. Run `python build.py`

This writes `Packages/ArtificerPermanentElixirs.pak` and a `.zip` containing it.

## Credits

- The Artificer class mod and its authors, for everything this patch builds on.
- Patch by LoneTitan01.
