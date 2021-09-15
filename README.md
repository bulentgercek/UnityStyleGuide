# Unity Style Guide (WIP)

This style guide was produced for Unity3D as a purpose and aims to create a common language with Unreal Engine.
For this reason, all style guides that are currently important in the market have been examined and common points
have been carefully determined. I am sure, it will be very useful for studios that use both Unity3D and Unreal Engine
and think it would be healthy to establish a certain joint bridge between the two.

Bulent Gercek | bulentgercek@gmail.com | [bulentgercek.com](http://www.bulentgercek.com)

## Inspirational Resources

*timdhoffmann* - [Unity Project Style Guide](https://github.com/timdhoffmann/unity-project-style-guide) | 
*Allar* - [Gamemakin UE4 Style Guide](https://github.com/Allar/ue4-style-guide)

<a name="1"></a>

## 1. Introduction Terminology

<a name="1.1"><a>

### 1.1 Spaces

* Never and ever use Spaces in folder, file or variable names.

<a name="1.2"><a>

### 1.2 Cases

* Use **PascalCase** for custom file and folder names. (E.g. DetailedSpecificObjectName)
Do not use spaces, underscores, or hyphens, except naming different aspects of the same thing.
Use underscores between the core name, and the thing that describes the "aspect". For instance:
  * GUI buttons states EnterButton_Active, EnterButton_Inactive
  * Textures BigRocket_Diffuse, BigRocket_NormapMap
  * Skybox CitySky_Top, CitySky_North
  * LOD Groups BigRocket_LOD0, BigRocket_LOD1

    Do not use this convention just to distinguish between different types of items, for instance
    Tree_Small, Tree_Large should be SmallTree, LargeTree.

* Use **camelCase** for **local** variables, e.g. carCount, rotateSpeed, thrustPower.
If its a **class** variable add underscore as the first letter, e.g. _rigidBody,_audioSource.

<a name="2"><a>

## 2. Asset Naming Conventions

Naming conventions should be treated as law. A project that conforms to a naming convention is able to have its assets
managed, searched, parsed, and maintained with incredible ease.

<a name="2.1"><a>

### 2.1 Base Asset Name

All assets should have a Base Asset Name. A **Base Asset Name** represents a logical grouping of related assets.
Any asset that is part of this logical group should follow the standard of **Prefix_BaseAssetName_Variant_Suffix**.

Keeping the pattern **Prefix_BaseAssetName_Variant_Suffix** and in mind and using common sense is generally enough to
warrant good asset names. Here are some detailed rules regarding each element.

**Prefix** and **Suffix** are to be determined by the asset type through the following **Asset Name Modifier** tables.

<a name="2.2"><a>

### 2.2 Asset Name Modifiers

<a name="2.2.1"><a>

#### 2.2.1 Most Common

| Asset Type       |Prefix | Suffix     | Notes |
| ---------------- | ----- | ---------- | ----- |
| Scene / Level    | SC_   |||
| Level (Lighting) | LS_   |||
| Mesh             | SM_   |||
| Material         | MA_   |||
| Texture          | TT_   |||
| Prefab           | PF_   |||
| Particle System  | PS_   |||
| Audio Clip       | AC_   |||
| Animation Clip   | ANC_  |||
| JSON Text File   | TXT_  |||

<a name="2.2.2"><a>

#### 2.2.2 Textures

| Asset Type                          | Prefix | Suffix     | Notes            |
| ----------------------------------- | ------ | ---------- | -----------------|
| Texture (Editor)                    | TT_    | _ED        | Unity Editor GUI |
| Texture (Sprite)                    | TT_    | _SP        | 2D and UI        |
| Texture (Cursor)                    | TT_    | _CR        ||
| Texture (Cookie)                    | TT_    | _CK        ||
| Texture (Diffuse/Albedo/Base Color) | TT_    | _Diffuse   ||
| Texture (Normal Map)                | TT_    | _Normal    ||
| Texture (Mask)                      | TT_    | _Mask      ||
| Texture (Alpha/Opacity)             | TT_    | _Alpha     ||
| Texture (Bump)                      | TT_    | _Bump      ||
| Texture (Specular)                  | TT_    | _Specular  ||
| Texture (Ambient Occlusion)         | TT_    | _AO        ||

<a name="3"><a>

### 3. Project & Hierarchy Structures

<a name="3.1"><a>

#### 3.1 Project Structure Principles

<a name="3.1.1"><a>

* **Prefab everything**.
  * To modify an asset from the store, drag it into the hierarchy and create a prefab inside _Project.

* **Use the Project tab's *search* functionality**:
  * *Search by Type* in the *upper right*.
  * *Restrict results to selected folder only* (recursively): Click on *Search* and selecting the desired folder from
  the drop-down (operation mode will be remembered).

* **Save searches as *context sensitive filters*** (two colum layout):
  * Click on the *star* in the top right to save a search. The *filter will apply to any selected folder*, for example:
    * *Only scripts in selected* (and sub-folders)
    * *Only prefabs in selected* (and sub-folders)
    * *Only animations in selected* (and sub-folders)

* *Pin* folders by dragging them to *Favorites*.

* *Don’t* disassemble *context-specific assets*. For instance, leave the folder structure of downloaded assets intact.

* **Use Tags to mark imported 3rdParty assets:**
  * Select an item in the project browser and assign a tag in the bottom right of the inspector.
    * For entire packs, mark the top folder of the asset pack.
    * Assets that come as individual files can be marked directly.

* When working with assets from the asset store:
  * **Leave any complex asset package files, where they imported to by default.** This makes updating and keeping track easier.
  * **When making modifications**, copy the file(s) you want to modify (script, art, etc.), to an appropriate
  subfolder in *_Project*. **Make only changes to that copy** and make the other parts reference the newly
  created, modified file.

<a name="3.1.2"><a>

##### 3.1.2 Example Project Structure

<pre><p style="color:gray">Assets
    __NoVersionControl
    __Project
    |-- Commons
    |-- Actors
    |   |-- Cameras
    |   |   |-- PF_Camera_SplashScreen.prefab
    |   |   |-- PF_MainCamera.prefab
    |   |-- Structures
    |   |   |-- MA_LandingPad.mat
    |   |   |-- PF_LandingPad.prefab
    |   |-- Pawns
    |   |   |-- AC_RocketDeathExplosion.ogg
    |   |   |-- AC_RocketMainThrustEngine.ogg
    |   |   |-- MA_Rocket.mat
    |   |   |-- PF_Rocket.prefab
    |   |   |-- PS_RocketExplosion.prefab
    |   |   |-- PS_RocketMainThrust.prefab
    |   |   |-- SM_Rocket.fbx
    |   |   |-- TT_Rocket_BaseColor.png
    |   |-- Characters
    |   |   |-- Robocop
    |   |   |   |-- AC_Robocop_Victory.ogg
    |   |   |   |-- AC_Robocop_Death.ogg
    |   |   |   |-- MA_Robocop.mat
    |   |   |   |-- PF_Robocop.prefab
    |   |   |   |-- SM_Robocop.fbx
    |   |   |   |-- TT_Robocop_Diffuse.png
    |   |   |   |-- TT_Robocop_Normal.png
    |   |-- Terrain
    |   |   |-- MA_Ground.mat
    |   |   |-- MA_Obstacle.mat
    |   |   |-- PF_Ground.prefab
    |   |   |-- PF_Obstacle.prefab
    |   |-- Items
    |   |-- UI
    |   |   |-- Fonts
    |   |   |-- Icons
    |   |   |   |-- Main
    |   |   |   |   |-- TT_Project_Icon_64x64_SP.png
    |   |   |   |   |-- TT_Project_Icon_512x512_SP.png
    |   |   |   |-- Content
    |   |   |   |   |-- TT_Continue_Icon_SP.png
    |   |   |-- Buttons
    |   |   |   |-- Menus
    |   |   |   |-- Content
    |-- Environments
    |   |-- MA_Skybox.mat
    |-- Scenes
    |   |-- SC_Start
    |   |   |-- LightningData.asset
    |   |   |-- ReflectionProbe-0.exr
    |   |-- LS_Common.lighting
    |   |-- SC_Start.unity
    |-- Scripts
        |-- Managers
        |   |-- GameManager.cs
        |-- Pawns
        |   |-- RocketMovement.cs
        |-- Terrain
        |   |-- ObstacleOscillator.cs
</p></pre>

#### 3.2 Hierarchy Structure

This is an example hierarchy structure.

<pre><p style="color:gray">Main
Managers
Cameras
Lights
UI
|-- Canvas
|   |-- HUD
|   |-- PauseMenu
Gameplay
|-- Pawns
|-- Items
Place
|-- Props
|-- Structures
|-- Terrain
_DynamicObjects
</p></pre>
