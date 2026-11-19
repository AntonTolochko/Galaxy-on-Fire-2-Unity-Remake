# Scavenger: archived prototype and future external mod

Decision (2026-11-19): withdraw upstream PR #285. Scavenger is planned as an external mod in the future,
rather than a built-in game mode. This archive preserves the prototype for reference; it is not a completed
or installable external mod and must not be presented as one.

## Preserved implementation

- Original PR: https://github.com/JoppieToppie/Galaxy-on-Fire-2-Unity-Remake/pull/285
- Preserved source head: `4791eb778998be1744d16a7eb7f6fe752072bf2b`.
- Original fork branch: `feature/scavenger-custom-gamemodes`.
- Full gameplay specification and acceptance checklist: [scavenger-mode.md](scavenger-mode.md).
- Main rule implementation: `Assets/Scripts/Runtime/Game/ScavengerMode.cs`.
- Regression coverage: `Assets/Scripts/Tests/EditMode/Economy/ScavengerModeTests.cs`.
- Prototype menu integration: `MainMenuGamemodes.cs`; save grouping includes `SaveGroupPicker.cs`,
  `SaveGame`, `SaveTransfer`, `OriginalSaveTransfer` and `Session` changes.

The full parent tree is retained, including gameplay, menus, save isolation, translations, tests and notes.
Closing the PR does not mean these engine-level changes have been accepted upstream.

## Future port

Implement the mode as a separately distributed mod using the project's supported mod/Lua APIs. Inventory the
required hooks against the current upstream before reusing code: starting loadout and completed-world state,
shop stock restrictions, ordinary NPC cargo, blueprint availability, production-based Champion completion,
and isolated persistence/identity for the mode. The existing specification is the reference for intended rules.

Do not assume every prototype C# hook is already exposed to mods. Document missing API capabilities and propose
small general-purpose hooks separately if needed. Do not copy the prototype's save-format version or built-in
menu/save-group implementation blindly into a future release. Reassess compatibility with current saves,
import/export, New Game+, active mods and multiplayer authority. Multiplayer is outside the prototype's scope.

No gameplay implementation, save migration,
or external-mod packaging is added by this archival note. Validation claims in the original PR describe that
historical prototype, not a future mod or compatibility with today's upstream.
