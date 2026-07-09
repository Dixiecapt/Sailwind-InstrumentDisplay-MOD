# Instrument Display

A **minimal, customizable** ship-telemetry overlay for **Sailwind** that works on **stock and modded ships alike**.

Sailwind's world is diegetic and beautiful, so this HUD stays out of the way: five small, translucent panels that hug their own text, collapse to a single line with one click, borrow the game's own font, and read only what the ship is actually doing. Every panel and nearly every behavior is configurable, and several readings only appear when you carry the right instrument — a compass for heading, a chip log for speed, a wind indicator for wind.

> Instrument Display is a derivative of **BoatStatusHUD** by **luizbag**, reorganized and extended for broad ship compatibility. See *Credits* below.

## Features

Five collapsible groups. Click the small bullet at the left of any panel to fold it to a labelled strip; click again to expand.

- **Instruments** — Speed (needs a chip log aboard), Heading with compass point (needs a compass aboard), and Heel angle with side (e.g. `4.2 deg Stbd`).
- **Cargo** — Deadweight (everything the ship carries: cargo, crew, and the effective weight of any bilge water — never the hull itself), Freeboard (deck height above the water, counting down as you load), and Burden (a plain-word load rating: Light / Normal / Loaded / Overloaded).
- **Sounding** — Sea Depth and Keel Clearance, from a real depth-sounding beneath the hull.
- **Status** — Hull Integrity and Bilge Water, colour-coded as they worsen.
- **Weather** — Wind as a compass point and a sailor's word (Calm ... Gale; needs a wind indicator on the ship), and Conditions in one word (Fair / Moderate / Squally / Tempest), read from the game's own storm system.

## What makes it "works on all ships"

Readings are derived from the vessel's live physics and geometry rather than any hard-coded ship list: cargo is summed from the game's own item manifest, the water surface is sampled from the game's ocean, and the depth sounding and freeboard are measured from the hull's own collision geometry (in the boat's local frame, so heeling doesn't skew them, and with masts/rigging excluded so they don't masquerade as the deck). Stock hulls, the OldChronian ships, Shattered Seas, Leopard, Dinghies and others are pre-profiled for the Burden rating, and unknown ships fall back gracefully with an honest `(no profile)` marker instead of a bogus reading.

## Installation

**Automatic (recommended):** install via the Thunderstore App or r2modman — it will pull the BepInEx dependency for you.

**Manual:** install BepInEx 5.4.2100, then drop `InstrumentDisplay.dll` into `Sailwind/BepInEx/plugins/`.

> **Do not run Instrument Display and BoatStatusHUD at the same time.** They are two takes on the same overlay and will draw on top of each other. Use one or the other. (They no longer *block* each other — the two mods have separate identities — but running both just double-draws the HUD.)

## Configuration

Everything is adjustable in the in-game **Configuration Manager** (F1) or by editing
`BepInEx/config/com.dixiecapt.sailwind.marinershud.cfg` (the filename uses the mod's internal ID):

- **HUDSections** — master toggle, per-group visibility, and optional hotkeys (default `F8` shows/hides the whole HUD).
- **Appearance** — font (`auto` borrows Sailwind's own font, or name your own), font size, panel and text opacity, and a text drop-shadow for daylight readability.
- **EquipmentRequirements** — turn the compass/chip-log/wind-indicator gates on or off, and edit the item-name fragments each looks for.
- **ShipWeightProfiles** and **LoadStatusThresholds** — per-ship carrying capacities and where Light/Loaded/Overloaded fall. Matching is by the boat's internal name; enable `DebugMassReadout` to see that name plus the working figures.

## Credits

- Original mod: **BoatStatusHUD** by **luizbag** — https://github.com/luizbag/BoatStatusHUD
- This derivative — reorganization, all-ship compatibility work, and additional readings — maintained by **Dixiecapt**.

If the original author's project carries a license, this derivative is offered under the same terms; please refer to the upstream repository. Full credit for the original concept and implementation belongs to luizbag.
