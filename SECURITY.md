# Security Policy

## Security Hardening

This is a SudoWP security fork of the original Crowdsignal Forms plugin. The original plugin (versions <= 1.7.2) contained a **critical Missing Authorization vulnerability (CVE-2025-69015)** that allowed authenticated users to modify polls they do not own.

### Version 1.7.3 Security Improvements

This release includes the following security enhancements:

1. **CVE-2025-69015 Patch**: Restricted REST API management endpoints for Polls, Feedback, and NPS surveys to users with `edit_others_posts` capability
2. **Strict Type Enforcement**: Added `declare(strict_types=1);` to all PHP files for better type safety
3. **Input Sanitization**: All user inputs are properly sanitized using WordPress functions
4. **Output Escaping**: All outputs are properly escaped to prevent XSS attacks
5. **Nonce Verification**: CSRF protection implemented using WordPress nonces
6. **Capability Checks**: Proper authorization checks on all administrative functions

## Security Audit Results

### Code Security Review

A comprehensive security audit was performed on the codebase with the following findings:

#### ✅ Passed Checks

- **No Dangerous Functions**: No use of `eval()`, `exec()`, `system()`, `passthru()`, or `shell_exec()`
- **SQL Injection Prevention**: No direct database queries; uses WordPress APIs
- **XSS Prevention**: All outputs properly escaped with `esc_html()`, `esc_attr()`, `esc_url()`, etc.
- **CSRF Protection**: Nonce verification implemented on all state-changing operations
- **Input Sanitization**: All user inputs sanitized with `sanitize_key()`, `sanitize_text_field()`, `absint()`, etc.
- **Authorization Checks**: Proper capability checks (`current_user_can()`) on administrative functions
- **Secure HTTP Requests**: Uses `wp_remote_post()` instead of raw cURL

#### REST API Security

All REST API endpoints implement proper permission callbacks:

1. **Poll Management** (`/crowdsignal-forms/v1/polls`):
   - `create_or_update_poll_permissions_check()`: Requires `edit_others_posts` capability
   - Prevents unauthorized users from creating/modifying polls

2. **Feedback Management** (`/crowdsignal-forms/v1/feedback`):
   - `create_or_update_feedback_permissions_check()`: Requires `edit_others_posts` capability
   - Public response endpoint uses nonce verification

3. **NPS Management** (`/crowdsignal-forms/v1/nps`):
   - `create_or_update_nps_permissions_check()`: Requires `edit_others_posts` capability
   - Response endpoint includes checksum validation

#### Input Validation Findings

All `$_GET`, `$_POST`, and `$_REQUEST` usages are properly handled:

- **Settings Page**: Uses `wp_verify_nonce()` for form submissions
- **Admin Notices**: Parameters sanitized with `sanitize_key()`
- **Setup Process**: API keys sanitized with `sanitize_key()`
- **REST API**: Uses WordPress REST API framework with built-in sanitization

## Reporting a Vulnerability

If you discover a security vulnerability in this plugin, please report it to the SudoWP team:

- **Email**: security@sudowp.com (if available)
- **GitHub**: Open a security advisory on the repository

Please do **not** open public issues for security vulnerabilities.

## Security Best Practices for Users

1. **Keep Updated**: Always use the latest version of the plugin
2. **Restrict Permissions**: Only grant `edit_others_posts` capability to trusted users
3. **Use HTTPS**: Ensure your WordPress site uses HTTPS to protect API communications
4. **Regular Backups**: Maintain regular backups of your WordPress database
5. **Monitor Logs**: Review server logs for suspicious API activity

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 1.7.3   | :white_check_mark: |
| 1.7.2   | :x: (Vulnerable)   |
| < 1.7.2 | :x: (Vulnerable)   |

## Credits

Security improvements and maintenance by the SudoWP community.
