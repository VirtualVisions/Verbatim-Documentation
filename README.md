# Verbatim Localization
![Verbatim Icon](https://github.com/VirtualVisions/Verbatim-Documentation/blob/main/Images/ReadMe%20Banner.png)

[License](https://github.com/VirtualVisions/Verbatim-Documentation/blob/main/license.md)

Verbatim is a localization tool for VRChat worlds and the content in them.
It provides a single, centralized system for managing content, features, and settings for VRChat worlds based on the user's preferred language.

---
### Language Manager
![Language Manager](https://github.com/VirtualVisions/Verbatim-Documentation/blob/main/Images/LanguageManager.png)
![Language Manager](https://github.com/VirtualVisions/Verbatim-Documentation/blob/main/Images/LocalizationManagerComponent.png)

The "Verbatim Language Manager" is the main prefab that will add localization to your world.
It comes with the data object (By default named "Example Localization Data", and can be swapped out at any time), as well as the language selection panel.
This is what users will primarily interact with to set their current language, and comes in Normal and Dark modes.

You can find it at **Packages -> Verbatim Localization -> Runtime -> Prefabs**.

---

### Verbatim Window
![Verbatim Window](https://github.com/VirtualVisions/Verbatim-Documentation/blob/main/Images/VerbatimWindow.png)

The Verbatim Window is how you will be interfacing with your localization data.
This allows you add languages, keys of various types, and set their corrosponding values.
To get started, go to the **Options** menu on the top right and click **"Create New Data"**, or simply select an existing one in the selector on the top left.

The Options menu has various actions that you can perform:

| Option | Description |
| ----------- | ----------- |
| Documentation | Opens this page of documentation on GitHub. |
| Create new Data | Creates a new Localization Data object and automatically selects it. |
| Find Data in Scene | Finds any Localization Manager in the scene and selects the Data it is currently using. |
| Set Manager Data to selected | Sets the scene's Localization Manager's Data to the one currently selected. |
| Use Language Dropdowns | Toggles whether the language fields should use the custom dropdown field. |
| Use Key Dropdowns | Toggles whether the language fields should use the custom dropdown field. |
| Add VRChat languages | Adds all languages currently supported by VRChat. |
| Sort Languages | Sorts all languages alphabetically. |
| Json > Import from File | Imports StringKey values from a provided Json file. |
| Json > Export to File | Exports StringKey values to a Json file. |
| CSV > Import from File | Imports StringKey values from a provided CSV file. |
| CSV > Export to File | Exports StringKey values to a CSV file. |

**"Keys"** are what you select from when localizing your data.
Each key has a name, which will be what all localization components reference.
Additions and other changes to the provided languages are automatically applied to all keys.
There are six different variable types that can be stored as keys:
- Strings
- Sprites
- Textures
- Materials
- Urls
- Audio

Keys have a value for each language, as well as a Fallback value.
If a value is not provided or is empty for a given language, it will instead use the Fallback value.

---

### Localization Component
![Verbatim Window](https://github.com/VirtualVisions/Verbatim-Documentation/blob/main/Images/LocalizationComponents.png)

These components are the primary ways you will be using Verbatim.
Each one allows you to select a key that will affect it's corrosponding component.
You also have the toggle **"Enable Only For Selected Language"**, which will disable/clear the component when the selected language below is not the actively selected language.

| Component | Description |
| ----------- | ----------- |
| Verbatim Audio | Swaps audio clips on an Audio Source. Can be set to play on language change. |
| Verbatim GameObject | Toggles the GameObject on only for a selected language. |
| Verbatim RawImage | Swaps a texture in a RawImage UI component. |
| Verbatim Renderer | Swaps materials on a renderer. An array of keys is provided for renderers that require more than one material. |
| Verbatim Sprite | Swaps a sprite on an Image UI component. |
| Verbatim Text | Changes the text on a Unity Text component to a given string. |
| Verbatim TextMeshPro | Changes the text on a TextMeshPro component to a given string. |
| Verbatim TextMeshPro (UI) | Changes the text on a TextMeshPro UGUI component to a given string. |
| Verbatim Video Player - AVPro | Swaps urls on an AVPro Video Player. Can be set to play on language change. |
| Verbatim Video Player - Unity | Swaps urls on a Unity Video Player. Can be set to play on language change. |

---
### Custom Implementation

Lots of tools are provided to let you expand off of for your own implementation.
Making your own Localization Component is as simple as inheriting from **"BaseLocalizationComponent"**, though other tooling can be made easily by inheriting from **"LanguageChangedListener"**, which is the class that is collected during build for the manager to call back to.

Two attributes have been added for selecting languages and keys in the inspector: **[VerbatimLanguage]** and **[VerbatimKey]** respectively.
These custom editors can be disabled from the Verbatim Window's options menu.
The selection menu can be more difficult to use with very large amounts of keys depending on your screen size, so the option to disable them was added.

A scripting define symbol "VERBATIM" is included in any projects implementing Verbatim Localization, so tools utilizing Verbatim-specific code can have that code disabled for projects that do not include it.