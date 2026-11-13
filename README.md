# ClassNameTypePairs Client-In-Game Creatable Extended

Useful for adding Types to Functions & Type Functions, inspired by reactive UIs on Roblox!

**[This API-Dump](<https://github.com/MaximumADHD/Roblox-Client-Tracker/blob/roblox/Full-API-Dump.json>)** is used to generate the module;

The version is derived from the commit name, the latest version entry inside of **[version-history.json](<https://github.com/MaximumADHD/Roblox-Client-Tracker/blob/roblox/version-history.json>)** file included in the same commit or manually determined by a human.

Whenever **[this API-Dump](<https://github.com/MaximumADHD/Roblox-Client-Tracker/blob/roblox/API-Dump.json>)** has a commit, that the above is missing, it might be used for generation instead, e.g. the above only starts from version `0.563.0.5630392` and this one can cover everything from way back around `0.353.0.236588`

The module header will always disclose the link to the file used for generation, the found version in its initial format and the **[formatted variant of the version as per description below](#section-this-is-required-to-perform-wally-publish)**.

The module header is also likely to contain important links, such as links to the current release!

## Promises
### Section: This is required to allow for safe usage of ANY version of this module (``@*``).

This module shall NEVER have anything functional except
- A header comment with relevant links
- ``export type`` definition for "***ClassNameTypePairs***", "***ClassNameTypePairsLeaf***", "***ClassNameTypePairsChild***", and all of the other ClassName - Child, Descendant and Leaf relationships as described below
- Return of the return value `return table.freeze({})`
    > *Why does it return an empty table and not ``nil`` or ``true`` for example?*
    >
    > Because nnullcolumn (1477070619685294270) asked on Discord!
    >
    > "*please change the return type back to table.freeze({})*
    > 
    > *my codebases do not allow returns other than tables 😔*"

The contents of **[src/init.luau](src/init.luau)** are automatically generated from the **(special thanks to) [Roblox API Dump (the Roblox-Client-Tracker by MaximumADHD)](https://github.com/MaximumADHD/Roblox-Client-Tracker)** and must not be manually edited.
> The auto-generation script is part of [CoffeeBuildr](<https://github.com/Coffilhg/CoffeeBuildr>)

### *"**ALL CLASS NAMES**"* refers to all ClassNames that can be used with ``Instance.new()`` as in ``Instance.new(ClassName)`` without an error on a client-side script in-game.
There is a difference between allowed ``Instance.new()``'able ClassNames on the server and the client, as well as in-game vs Roblox Studio.
### This module is a successor of [CNTPClientInGameCreatable](<https://github.com/Coffilhg/ClassNameTypePairsClientInGameCreatable>), both will be maintained!

Every ClassName that has errored when used as ``Instance.new(ClassName)`` is listed in the [Missing.md](<Missing.md>)

### What's "Extended" about it?
[CNTPClientInGameCreatable](<https://github.com/Coffilhg/ClassNameTypePairsClientInGameCreatable>) only makes the per-ClassName ``export type {ClassName}Child``, ``export type {ClassName}Descendant`` and ``export type {ClassName}Leaf`` definitions for ClassNames that are creatable themselves.

However this wasn't really intended, this module addresses that flaw by making them for **every** ClassName that has children, creatable or not, e.g. ``GuiBase2d`` can't be ``Instance.new()``'d, yet ``GuiBase2dChild``, ``GuiBase2dDescendant`` and ``GuiBase2dLeaf`` are still here, because ``GuiBase2d`` has valid children, descendants & leaves.

> *This was the main goal initially - have a list of all ClassNames and a list of all UI ClassNames to assist Reactive UI libraries on Roblox keep up without having to manually maintain this dictionary*

This module only guarantees backwards-compatibility for three type definitions:
- `ClassNameTypePairs`
> ALL CLASS NAMES (as intended initially)
- `ClassNameTypePairsLeaf`
> represents ALL CLASS NAMES that have no children, thus each of them is a leaf
- `ClassNameTypePairsChild`
> represents ALL CLASS NAMES that are roots (in other words child classes of the roblox studio hierarchy, this is just `Object`, but the auto-generator will add (detect) more if roblox ever makes such update)

these type definitions are guaranteed to be present, regardless of the module version, however their contents are not going to be consistent, or are, but only as much as Roblox allows them to.

When Roblox removes a ClassName (e.g. it was deprecated and removed), that ClassName will no longer be included in releases of this module, except in the versions of the module, that've captured them before or will capture them again (if Roblox re-added them)!

### Section: This is required to perform `wally publish`

To achieve **[SemVer](<https://semver.org/>)** (i.e. **[Zer0Ver](<https://0ver.org/>)** in this case), the **Major Version** part will be removed if 0, otherwise amplified:

e.g. `0.736.0.7361342` -> `736.0.7361342`

if **Major Version** ever becomes > 0, multiply `its value * 1_000_000` and add with the beginning (the *Minor Version*), e.g. `1.736.0.7361342` -> `1000736.0.7361342` because `1_000_000 + 736 = 1000736`

in the cases when a version repeats on the **[Roblox Client Tracker](<https://github.com/MaximumADHD/Roblox-Client-Tracker>)** and the changes are reasonable to keep they'll be split into the newest one with version of ``V`` and every other one of the same version as ``V-rc.X``, however using ``@*`` or ``^`` for wally dependency version will never pick a pre-release, so if you need it, it must be explicit in your ``wally.toml``

---

## Available Here!
- **[This repository](src/init.luau) ~ [src/init.luau](src/init.luau)**
- **[Wally](<https://wally.run/package/coffilhg/classnametypepairsclientingamecreatableextended>)**

    ```toml
    ClassNameTypePairsClientInGameCreatableExtended = "coffilhg/classnametypepairsclientingamecreatableextended@*"
    ```
<!-- CoffeeBuildr:Rotriever -->
- **[Rotriever](<https://github.com/Coffilhg/ClassNameTypePairsClientInGameCreatableExtended/releases/tag/v387.0.306142>)**

	```toml
	ClassNameTypePairsClientInGameCreatableExtended = "github.com/Coffilhg/ClassNameTypePairsClientInGameCreatableExtended@387.0.306142"
	```
<!-- /CoffeeBuildr:Rotriever -->

---

# Dependencies
- None

---

## License & Attribution

This module is licensed under the **Unlicense License**.

> See [here](LICENSE) or [here to learn more](https://unlicense.org)

Stars are appreciated!