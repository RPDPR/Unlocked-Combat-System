<img width="1195" height="672" alt="UCS_splash" src="https://github.com/user-attachments/assets/48814236-7a5a-4f3e-ac9a-205fa0194874" />

# UnlockedCombatSystem

## About the Plugin

**UnlockedCombatSystem** is a lightweight C++ plugin built on the [Union Framework](https://gitlab.com/union-framework). It fully unlocks the combat system and its operations, providing developers with complete access to every stage of the damage calculation logic.
The plugin is primarily designed for **Daedalus** scripters, allowing them to modify engine-level combat functions directly from your scripts.

**Key Features:**
- Fully unlocked combat mechanics
- Access to all breakpoints in the damage calculations
- Minimal impact on original game's engine functions
- Compatible with Gothic I Classic and Gothic II NoTR

## Requirements
* **Gothic I Classic** or **Gothic II NoTR**
* **Union** version 1.0m or newer

---

# Quick Setup

### 1. Download
Download the latest version from [latest release](https://github.com/RPDPR/Unlocked-Combat-System/releases/latest) page.

Extract the archive. You will need specific files depending on your game version:
* **For Gothic 1:** Keep `UCS_g1.dll` and `UCS_logic.d`.
* **For Gothic 2 NoTR:** Keep `UCS_g2a.dll` and `UCS_logic.d`.
* The `Externals.d` file is required for valdation in compilators like Gothic Sourcer.

You can delete the rest of the files if you are sure that you will not need to modify another version of Gothic in the future.

> <img width="167" height="155" alt="!1" src="https://github.com/user-attachments/assets/3154a062-1000-4ff6-9893-8f24714a3aeb" />

### 2. Integration Methods

#### Method A: Rapid Injection
*Best for quickly adding the plugin to a pre-compiled game or mod.*

1. Copy `UCS.dll` and `UCS_logic.dll` into `\System\Autorun` folder of your Gothic directory.

#### Method B: Project Integration (Recommended)
*Best for modders building their own project from scratch or re-compiling gothic or mods.*

1. Copy `UCS.dll` into the `\System\Autorun` folder (preferably within a `.mod` or `.vdf` volume).
2. Open your project in **GothicSourcer**.
3. Add `UCS_logic.d` to your project. It's best to create a `\Utils` or `\Utilities` folder in the root of your project for this purpose, although this isn't required. Experienced scripters can choose the best location for this script based on their project's architecture:
   * Right-click your folder and select **"New script file"**.
   * Name it `UCS_logic.d` or whatever you like.

> <img width="139" height="148" alt="!2" src="https://github.com/user-attachments/assets/a39d9717-3180-44d3-90d7-6e5b5cd83c0d" />

4. Select the script position in the `.src` file. **Script Order Matters,** incorrect positioning may cause compilation errors. It's recommended to choose a position **after** constants, classes, and AI functions, which already should be loaded by this time, but **before** any `\Story` scripts.

> <img width="220" height="269" alt="!3" src="https://github.com/user-attachments/assets/96f0cab8-17c9-4923-9915-1ead1e299b60" />

5. Open the file you just created, in the GothicSourcer editor, copy the contents of the `UCS_logic.d` file that is in the UCS plugin archive you downloaded.

6. **Register External Functions:**
   * In GothicSourcer, go to **Help** -> **Show external functions**.
   * Open the provided `Externals.d` from the UCS plugin archive you downloaded.
   * Copy the function signatures and paste them into the editor's `Externals.d` file.

> <img width="563" height="206" alt="!4" src="https://github.com/user-attachments/assets/44b57332-0a1c-4be0-a36c-362b109ea84c" />

7. **Compile:** Build your project as usual.

---

### 3. Done!
You are ready to go. Write your custom code, implement the best ideas inside `UCS_logic.d` and enjoy the results!


<img width="1672" height="940" alt="UCS_2 0_Banner1" src="https://github.com/user-attachments/assets/e02a5c27-fb0e-4426-ba12-361912167ea8" />

# UnlockedCombatSystem (UCS)

## About the plugin

**UnlockedCombatSystem** is a powerful C++ subsystem built on the [Union Framework](https://gitlab.com). It integrates directly into the **ZenGin** engine to fully unlock the combat logic for Gothic I Classic, Gothic II: Night of the Raven, and massive mods like *Legend of Ahssun*. 

The subsystem is designed specifically for Daedalus scripters, allowing you to bypass native engine limitations and control combat mechanics directly from your `.d` files.

## Key Features

### ⚔️ Damage Pipeline (Legacy v1.0 Core)
* Full access to all internal engine damage calculation stages.
* Custom interception breakpoints inside core combat routines.
* Minimal impact on original game performance and vanilla logic.

### 🧪 Advanced FX Engine (New in v2.0)
* Dedicated built-in engine to safely process periodic (Loop) and instant effects.
* Perfect for custom mechanics like realistic poisons, burning, or magic debuffs.
* Automated state machine that fully handles effect lifecycles under the hood.

### 🕹️ Runtime FX Control (New in v2.0)
* Over 20+ new external functions (getters and setters) for your scripts.
* Change running effects on the fly based on specific script events.
* Hot-swap active PFX visuals, adjust tick intervals, or rewrite the whole FX chain.

### 🎯 Flawless NPC Targeting (New in v2.0)
* Instant access to exact, real-time memory pointers for attackers and victims.
* Uses direct `UCS_GetDamageSender` and `UCS_GetDamageReceiver` calls.
* Completely fixes v1.0 bugs where identical monsters (e.g., multiple Wolves) break contexts.

### 💾 Save-Safe Architecture
* Complete memory cleanup and safety checks implemented in C++.
* Seamless state preservation across save game updates and load triggers.
* No access violations or crashes when passing expired or invalid data.

## Requirements
* **Gothic I Classic** or **Gothic II NoTR**
* **Union** version 1.0m or newer

---

## Quick Setup (v2.0)

### 1. Download
Download the latest version from [latest release](https://github.com/RPDPR/Unlocked-Combat-System/releases/latest) page
that matches your game version (**Gothic 1** or **Gothic 2 NoTR**).

Extract the archive. Each one contains:
* `UCS_gXX.dll` — Core subsystem library.
* `UCS_Consts_gXX.d` & `UCS_OnDamage_gXX.d` — Baseline setup scripts.
* `README.txt` & `Externals.d` — Full SDK documentation reference and compiler definitions.

You can delete the rest of the files if you are sure that you will not need to modify another version of Gothic in the future.

> <img width="149" height="172" alt="image" src="https://github.com/user-attachments/assets/73a6e0f3-970b-47c3-96ab-d181dbafa36b" /> <img width="155" height="177" alt="image" src="https://github.com/user-attachments/assets/ea785dcd-7a50-4ef5-8408-9ecc09bab0cb" />



### 2. Integration Methods

#### Method A: Rapid Injection
*Best for quickly integrating the UCS to a pre-compiled game or mod.*

1. Copy `UCS_Consts_gXX.d`, `UCS_OnDamage_gXX.d` and `UCS_gXX.dll` into `\System\Autorun` folder of your Gothic directory.
2. Start the game and check it out!

#### Method B: Project Integration (Recommended)
*Best for modders building their own project from scratch or re-compiling gothic or mods.*

#### Manually:

1. Copy the core dynamic library `UCS_gXX.dll` into your game's `\System\Autorun\` folder (preferably packed within a `.mod` or `.vdf` volume for a final release).
2. In your project's directory (`_Work\Data\Scripts\Content\`), create a new folder named `UCS`.
3. Extract `UCS_Consts_gXX.d` and `UCS_OnDamage_gXX.d` from the downloaded archive into this newly created `UCS` folder.
4. Open your main `Gothic.src` file and register the scripts. **⚠️ Strict compilation order is required:**
   * Insert the constants path `UCS\UCS_Consts_gXX.d` strictly after  `_Intern\Constants.d` and `_Intern\Classes.d`
   * Insert the pipeline path `UCS\UCS_OnDamage_gXX.d` right after `UCS\UCS_Consts_gXX.d`.

> <img width="284" height="251" alt="image" src="https://github.com/user-attachments/assets/b0113b7d-0251-49ae-97fd-bda680bce8ff" />

5. Save file changes and go check it out to the game that all is made correctly!

#### Via Gothic Sourcer:
1. Copy `UCS_gXX.dll` into the `\System\Autorun` folder (preferably within a `.mod` or `.vdf` volume).
2. Open your project in **GothicSourcer**.
3. Add `UCS_Consts_gXX.d` and `UCS_OnDamage_gXX.d` files to your project. It's best to create a `\UCS` folder in the root of your project for this purpose:
   * Right-click your folder and select **"New script file"**.
   * Select the script position in the `.src` file. **Script Order Matters,** incorrect positioning may cause compilation errors.
   * It's required to choose a position **after** Constants.d and Classes.d files. `UCS_Consts_gXX.d` should go earlier than `UCS_OnDamage_gXX.d`.
5. **Register External Functions:**
   * In GothicSourcer, go to **Help** -> **Show external functions**.
   * Open the provided `Externals.d` from the archive, copy its contents, and append them to the compiler definitions.
6. **Compile** your project as usual.

---

## FX Prototype Initialization

UCS v2.0 introduces a native engine startup callback. Inside your script files, utilize `UCS_Init()` to define your blueprints. This is the best place to call prototype registrations:

```c
func void UCS_Init()
{
    // Automatically triggered by C++ core on game startup
    UCS_CreateFXProto(MyPoisonProto, 10, oEDamageIndex_Blunt, -1, "PFX_POISON", 0, 1000.0, 5, -1);
}
```

---

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.


