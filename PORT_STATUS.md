# Regrowth NeoForge 26.1.2 — DEV2 status

This is the REAL 1.21.11 NeoForge source branch upgraded at the build configuration level, NOT a runnable release.

## Changes made
- Retained all 26 original Java source files and assets, instead of using Forge code.
- Updated MC to 26.1.2, NeoForge coordinate to provisional 26.1.2.124 (must verify availability), Java toolchain to 25, MDG to 2.0.148, version labels to dev2.
- Removed stale 1.21.11 Parchment setup because 26.1 uses unobfuscated source parameter names.
- Preserved native NeoForge event handlers; no Connector, Fabric API or Fabric classes.

## Not yet done
- No successful compilation or Minecraft test. Installed JDK is 21, dependency resolution unavailable in this runtime.
- Existing Minecraft API method calls and registry references must be compiled against 26.1.2 and adjusted from compiler diagnostics.
- Confirm the NeoForge version coordinate; the selected one is provisional.
- Review event behavior after port, particularly path repair/walls and action coordinator.
- Source includes original author's license; retain attribution and license on redistribution.

## Build
Install JDK 25, then run `./gradlew clean build --stacktrace` on an internet-connected machine. Record all compilation errors and fix API incompatibilities before using generated JAR in the game.
