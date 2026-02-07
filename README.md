# SudoWP Crowdsignal Forms

![PHP Version](https://img.shields.io/badge/PHP-%3E%3D%208.2-777bb4.svg)
![License](https://img.shields.io/badge/License-GPLv2%2B-blue.svg)
![Status](https://img.shields.io/badge/Status-Security%20Hardened-green.svg)

**This is a SudoWP security fork of the original Crowdsignal Forms plugin.**

> [!WARNING]
> **Security Notice**: The original "Crowdsignal Forms" plugin (versions <= 1.7.2) contains a **critical Missing Authorization vulnerability (CVE-2025-69015)** allowing authenticated users to modify polls they do not own. This SudoWP edition patches this vulnerability.

## Installation

1.  **Deactivate** the original Crowdsignal Forms plugin.
2.  **Delete** the original Crowdsignal Forms plugin to avoid conflicts.
3.  **Install** and **Activate** `SudoWP Crowdsignal Forms`.

## Changelog

### 1.7.3 - SudoWP Security Release
*   **SECURITY**: Patched CVE-2025-69015. Restricted REST API management endpoints for Polls, Feedback, and NPS surveys to users with `edit_others_posts` capability.
*   **FEATURE**: Added action hooks for form creation/updates (`crowdsignal_forms_poll_created`, etc.) to support integrations (e.g., Bit Integrations).
*   **MODERNIZATION**: Enforced strict typing (`declare(strict_types=1);`).
*   **BRANDING**: Updated identity to SudoWP.

## Disclaimer

This plugin is maintained by the SudoWP community to provide security patches for abandoned or vulnerable plugins.
