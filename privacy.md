# Privacy Policy — MigVPN

_Last updated: 2026-06-08_

## What we collect

MigVPN ("we", "the service") is a paid VPN. To provide the service we store
the following information, and only the following information:

1. **Subscription identity.** A 16-character licence key issued at purchase,
   the plan it is on (trial / monthly / yearly), and its expiry timestamp.
   We hash the key (HMAC-SHA256) before storing it; the cleartext key lives
   only in your device's Keychain.
2. **Account binding.** If you bought through our Telegram bot, your
   Telegram user ID (numeric) and username (if public) are linked to the
   licence key for support and renewal purposes.
3. **Device binding.** A stable per-install UUID (Apple's
   `identifierForVendor`) is associated with the licence to prevent
   simultaneous use on multiple devices.
4. **Provisioning material.** A WireGuard public key, a server-assigned
   internal IP (10.10.1.x), and a preshared key for the tunnel. The
   private key is encrypted at rest (AES-256-GCM) with a key kept in a
   separate secret store from the database.
5. **Liveness signal.** A `last_seen_at` timestamp that updates each time
   your client checks in, so we can detect inactive accounts.

## What we do NOT collect

- **Traffic.** We do not log, inspect, or store the contents of any
  packets that pass through the VPN.
- **Browsing history.** We do not collect URLs, hostnames, DNS queries,
  destination IPs, or any record of what you connect to through the
  tunnel.
- **Bandwidth attribution.** We do not retain per-user byte counters or
  session-by-session usage logs.
- **Crash/analytics SDKs.** The app does not embed third-party trackers,
  advertising IDs, AppsFlyer, Firebase Analytics, or Apple's
  `AppTrackingTransparency` framework.

## How we use it

We use the items in "What we collect" only to:
- validate your subscription is active when you connect,
- issue new credentials on app reinstall using the same licence key,
- send renewal/expiry reminders via the Telegram channel you used to buy,
- prevent account sharing across more devices than the plan allows.

We do not sell, rent, share, or otherwise disclose this information to
third parties, advertisers, or data brokers.

## Where data lives

- **PostgreSQL** on a server we control in Tallinn, Estonia.
- **Encrypted backups** are taken daily and rotated at 30 days.
- The Telegram bot stores no message history outside its own Telegram
  account; we do not export Telegram conversations.

## Retention

- Active subscriptions: stored until the user requests deletion OR 30
  days after the subscription expires.
- Expired subscriptions: anonymised after 30 days (key hash kept for
  reissue, all Telegram and device bindings dropped).
- Server VPN peer block: removed automatically by the expiry sweeper
  when the subscription lapses.

## Your rights

You may at any time:
- Request a full export of your stored data (email below).
- Request immediate deletion (`/delete` in the Telegram bot, or email).
- Revoke the active device and reissue credentials to a new install.

## Contact

Telegram: `@mig_support`
Email: `legal@mig.app`

This policy is provided in English; the Russian translation hosted at the
same path is informational, and the English version governs in case of
discrepancy.
