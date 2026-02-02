=== SudoWP Crowdsignal Forms ===
Contributors: SudoWP, WP Republic
Tags: polls, forms, surveys, gutenberg, block, security, sudowp
Requires at least: 6.0
Requires PHP: 8.2
Tested up to: 6.8
Stable tag: 1.7.3
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

This is SudoWP Crowdsignal Forms, a community-maintained and security-hardened fork of the abandoned "Crowdsignal Forms" plugin.

== Description ==

This is SudoWP Crowdsignal Forms, a community-maintained and security-hardened fork of the abandoned "Crowdsignal Forms" plugin.

**Why this fork?**
This fork fixes a critical Missing Authorization vulnerability (CVE-2025-69015) present in the original plugin versions <= 1.7.2. The original plugin allowed authors to modify polls they did not own due to insufficient permission checks.

**Security Patches in SudoWP Edition:**
*   **CVE-2025-69015 Patch**: Restricted Poll, Feedback, and NPS survey management endpoints to users with `edit_others_posts` capability (Editors/Admins), preventing Insecure Direct Object Reference (IDOR) attacks by lower-level authenticated users.
*   **Strict Typing**: Enforced PHP `strict_types=1` across key files for better reliability.

The SudoWP Crowdsignal Forms plugin allows you to create and manage polls right from within the block editor, now securely.

== Installation ==

1. Deactivate and delete the original Crowdsignal Forms plugin.
2. Upload the `sudowp-crowdsignal-forms` folder to the `/wp-content/plugins/` directory.
3. Activate the plugin through the 'Plugins' menu in WordPress.

== Changelog ==

= 1.7.3 =
*   **SECURITY**: Patched CVE-2025-69015 (Missing Authorization) by restricting sensitive REST API endpoints.
*   **FEATURE**: Added action hooks `crowdsignal_forms_poll_created`, `crowdsignal_forms_poll_updated`, `crowdsignal_forms_feedback_upserted`, and `crowdsignal_forms_nps_upserted` for better 3rd-party integration.
*   **MODERNIZATION**: Renamed to SudoWP Crowdsignal Forms.
*   **MODERNIZATION**: Added strict type declarations.

== Upgrade Notice ==

= 1.7.3 =
This is a critical security release patching CVE-2025-69015 (Missing Authorization). It also adds new developer hooks for integrations. Immediate update is recommended.
