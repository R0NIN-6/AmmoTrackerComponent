
# AmmoTrackerComponent (Unreal Engine 5.7 C++ Plugin)

## Description
AmmoTrackerComponent is a lightweight Unreal Engine 5.7 C++ plugin intended to provide an easy, reusable way to track ammo counts for weapons (e.g., current ammo, reserve ammo, max capacity) via a component that can be attached to weapon actors.

Typical uses:
- Centralize ammo state on a weapon actor (or pawn)
- Expose ammo values to UI (HUD/UMG)
- Provide a single place to implement reload/consume/restore rules

> Note: This README focuses on installation and basic setup. Adapt the usage to match your project’s weapon architecture.

## Requirements
- Unreal Engine 5.7
- The "Gameplay Abilities" engine plugin must be enabled
- Optional: Visual Studio 2022 with the “Game development with C++” workload (Windows) for expanding the codebase

## Installation

### Option A: Install to a project (recommended)
1. Close the Unreal Editor.
2. Create a `Plugins` folder in your project root if it doesn’t already exist:
	- `<YourProject>/Plugins/`
3. Copy the plugin folder into your project:
	- `<YourProject>/Plugins/AmmoTrackerComponent/`
4. Right-click your `.uproject` and select **Generate Visual Studio project files**.
5. Open the generated `.sln` and build the project (Development Editor / Win64).
6. Launch the project. If prompted to rebuild modules, choose **Yes**.
7. In Unreal Editor, go to **Edit → Plugins**, find the plugin, and enable it if needed.
8. Restart the editor when prompted.

### Option B: Install to the engine (shared across projects)
1. Close the Unreal Editor.
2. Copy the plugin folder into your engine installation:
	- `<UE_5.7>/Engine/Plugins/Marketplace/AmmoTrackerComponent/`
	- (If `Marketplace` doesn’t exist, create it.)
3. Rebuild the engine/plugin as needed (or let the editor prompt you to build).
4. Enable the plugin via **Edit → Plugins** and restart the editor.

## Verify it’s working
- Open Unreal Editor → **Edit → Plugins** and confirm the *Ammo Component* plugin is listed and enabled (also make sure *GameplayAbilities* is enabled).
- In the **Add Component** menu for your Base weapon Blueprint, confirm the ammo-tracking component (Display name is *WeaponComponent*) entry appears and add it.
- Confirm the Starting Ammo properties are now exposed, these values should be set in your Child weapon blueprints (set image here)

- To initialize the component, an Ability System component is required on your Base pawn class. Add one, and then call the 'Initialize with ASC' function (add image)

- In your firing logic, use the "Can Weapon Fire" function to check if ammo is available (add image)
  

- Next, add the "Consume Ammo" node in your firing logic (add image)

- For reloading, map the "Reload" function to the key of your choice (add image)

- To integrate with UI, use the built-in Ammo Subsystem to retrieve the player's Ammo and Magazine count (add image)

## Troubleshooting
- If you see “Missing modules” on startup: regenerate project files and rebuild in Visual Studio.
- If the plugin doesn’t appear: confirm the plugin folder is in the correct `Plugins` path and that it contains a valid `.uplugin` file.
- If builds fail after moving between engine versions: delete `Binaries/` and `Intermediate/` for the plugin and rebuild.



