# Portal Studio

A dedicated desktop launcher for a private Minecraft: Java Edition modpack and community server.

**Status:** Under development and testing. Microsoft authentication integration requires verification with the application's own Client ID. The application is not presented as approved by Microsoft or Mojang.

## About the project

Portal Studio aims to simplify joining our Minecraft community. Players install the launcher, download the required modpack, sign in with their Microsoft account, and launch Minecraft with the community server configured.

The launcher is built with Electron and Node.js and is designed for a single community modpack.

This repository provides public information about the application and its authentication requirements. It does not currently provide a public installer.

## Features under development and testing

- A dedicated interface with a Play / Update button.
- Incremental modpack updates with file integrity checks.
- Digitally signed distribution manifests.
- Microsoft sign-in through the OAuth 2.0 Device Authorization Grant.
- Local encrypted storage of Microsoft refresh tokens.
- Minecraft launch with the community server as the connection destination.
- Fabric and Forge support for supported Minecraft versions.
- Configurable memory allocation, update notes, and launcher background.
- Protected administration tools for publishing modpack updates.

End-to-end testing with an authorized Microsoft account, the final modpack, and the community server is still required.

## Microsoft authentication and API access

Portal Studio uses its own Microsoft Entra application registration.

The authentication flow is:

1. The launcher displays a Microsoft device authorization code.
2. The player authorizes the application on Microsoft's website.
3. The launcher authenticates through Xbox Live and XSTS.
4. The launcher requests a Minecraft Services access token and the player's Minecraft: Java Edition profile.
5. The authorized session is used to launch Minecraft.

Access to the Minecraft Services authentication and profile APIs is required to complete this process.

Players must have valid access to Minecraft: Java Edition. Portal Studio does not provide offline authentication or bypass game ownership requirements.

## Security

- Microsoft account passwords are entered on Microsoft's website, not collected by the launcher.
- Refresh tokens are stored locally using Electron's operating-system-backed encryption.
- Authentication tokens are not exposed to the renderer interface.
- Modpack files are checked against their expected hashes.
- Distribution manifests are verified using a configured public key.
- Administrative credentials and private signing keys are excluded from the packaged client.

Credentials, authentication tokens, private signing keys, and player data must never be uploaded to this repository.

## Project contact

Questions about this application can be submitted through this repository's Issues section. Please do not include passwords, active authorization codes, or authentication tokens.

## Disclaimer

Portal Studio is an independent community project. It is not an official Minecraft product and is not affiliated with, endorsed by, or approved by Mojang or Microsoft.

Minecraft and related names belong to their respective owners.
