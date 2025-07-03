# [Autodownload Godot](https://github.com/hedberg-games/autodownload-godot)

A project template that automatically installs the correct version of Godot for your C# project.

## Quick Start

Fork and download [the repository](https://github.com/hedberg-games/autodownload-godot)

Open the solution in your favorite IDE.

Build the solution to automatically download Godot. 

Share with collaborators - anyone who builds it will automatically get the correct Godot version.

## Features
- Automatically downloads the [Godot editor](https://godotengine.org/) during build
- Includes [launch settings](https://docs.godotengine.org/en/stable/tutorials/scripting/c_sharp/c_sharp_basics.html#doc-c-sharp-setup-external-editor) to run and debug right from the IDE

## Supported Platforms

| OS | Architecture | Testing |
|---------|---------------|-----------|
| Windows | Intel (64 Bit) | :heavy_check_mark: Verified | 
| Windows | ARM (64 Bit) | Untested | 
| Linux | Intel (64 Bit) | :heavy_check_mark: Verified |
| Linux | ARM (64 Bit) | Untested |
| Mac (OSX) | Intel (64 Bit) | Untested |
| Mac (OSX) | ARM (64 Bit) | Untested |
| Any | 32 Bit | :x: Not Supported |

### Untested Platforms
Any platforms marked "Untested" are presumed to work, but have not yet been verified.

If you use one of these, please open an issue to report whether it works.

### 32-bit Architectures
Although Godot provides binaries for 32-bit architectures, this template does not currently support them. If you need one, please open an issue.

### Building in the Cloud

Build agents that have access to MSBuild and run one of the supported operating systems are presumed to work, but may require additional setup.

Notably, [Export Templates](https://docs.godotengine.org/en/stable/tutorials/export/exporting_projects.html#export-templates) are not currently downloaded by `Autodownload Godot`.

## Launch Settings and Supported IDEs
This template is intended to make it easy to run godot directly from your IDE (Integrated Development Environment).

### VS Code and Visual Studio
The [recommended](https://docs.godotengine.org/en/stable/tutorials/scripting/c_sharp/c_sharp_basics.html#doc-c-sharp-setup-external-editor) `launch.json` and `tasks.json` (for [VSCode](https://code.visualstudio.com/download)) as well as `launchSettings.json` (for [Visual Studio](https://visualstudio.microsoft.com/)) are included in the project. Simply use the `Run` launch configuration.

It is also possible to launch the Godot Editor directly from these IDEs by selecting `Editor` as the launch target instead.

### Other IDEs
Follow [Godot's Guidelines](https://docs.godotengine.org/en/stable/tutorials/scripting/c_sharp/c_sharp_basics.html#doc-c-sharp-setup-external-editor) for setting up your IDE (if available.) 

To run/debug the project, set your IDE to launch `editor\Godot.exe` (Windows), `editor/Godot.app` (MacOS), or `editor/Godot` (Linux) with the current working directory set to the `project` folder.

To open the editor, use the same settings as above and add `-e` as a command argument.

## Selecting Godot Version

By default the template uses the latest stable version of Godot, and you can pull changes in order to keep up-to-date.

If you wish to use a specific version of Godot, you can update the `GodotConfiguration.props` file to import that version:
```xml
<!-- Use version 4.3 -->
<Import Project="official/4.3/GodotHashes.props"/>
```

Presets are provided for all minor versions of Godot (`4.0`, `4.1`, etc.) as well as a `4.x`, which is similar to latest, but won't change major versions (if/when Godot 5 is released.)

### Custom Godot Builds

With a little configuration, this template can be used to automatically download custom builds of Godot.

The `GodotRemote.props` file provides the URLs for the editor download (in zip file format.) 

The `GodotHashes.props` file defines the specific version number that will be downloaded, as well as the `SHA512` hash for each supported OS and architecture. 

Samples are provided in the `project/autodownload/custom` folder, which you can update as desired.