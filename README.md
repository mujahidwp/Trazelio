<h1 align="center">Trazelio – Migration Leftover URL Scanner</h1>

<p align="center"><b>Finds leftover localhost, staging and old-domain URLs in the WordPress database after a site migration.</b></p>

<p align="center">
  <a href="https://wordpress.org/plugins/trazelio-migration-leftover-url-scanner/"><img src="assets/download-wporg.svg" alt="Download on WordPress.org" height="36"></a>
</p>

<p align="center">Free WordPress plugin · Version 1.0.0 · GPLv2 or later</p>

> [!NOTE]
> Trazelio – Migration Leftover URL Scanner is officially distributed through **WordPress.org**. Please download, install and get updates from its [WordPress.org page](https://wordpress.org/plugins/trazelio-migration-leftover-url-scanner/) so you always have the latest reviewed version.

## About

After moving a WordPress site, the database is often still full of addresses that point somewhere else: the old domain, the staging copy, `localhost:8080`, a temporary hosting domain, or `http://` links that cause mixed content warnings. Search-and-replace tools can fix these, but only if you already know every address to look for.

**Trazelio finds them for you.** It scans post content, post meta, term meta and options, groups everything it finds by address, and shows exactly where each one is stored. You decide what to fix.

#### What it detects

- **Local / development addresses** – `localhost`, `127.0.0.1`, private network IPs, `.local`, `.test` and similar development domains.
- **Staging and temporary domains** – staging subdomains and temporary domains from common hosts (WP Engine, Kinsta, Cloudways, Pantheon, InstaWP, WordPress.com staging and more).
- **Other WordPress addresses** – links to `wp-content`, `wp-includes`, `wp-json` or `?p=` URLs on another domain. When a linked upload also exists in your own uploads folder, Trazelio marks the host as **“Old address of this site”**.
- **Insecure http:// links** – links to your own site over `http://` on an `https://` site.
- **Old server paths** – absolute folder paths from a previous server (for example `/home/olduser/` or `C:\xampp\`), reported so you can re-save the plugin settings that hold them.

URLs are found in every form WordPress stores them: plain, JSON-escaped (`https:\/\/old.com`, used by page builders such as Elementor) and URL-encoded.

#### Safe fixing

- **Preview first.** See how many values change and before/after examples. Nothing is written during a preview.
- **Serialization-aware.** Serialized arrays are unserialized, changed and serialized again, so string lengths stay valid. Values that contain custom PHP objects or broken serialization are skipped and listed, never corrupted. No code from other plugins is run while data is inspected.
- **Only the domain changes.** The scheme and host are replaced with your current site address; paths, query strings and file names stay the same.
- **Built-in backups and rollback.** Every changed value is copied to a backup table before it is written. A rollback restores each value, but only if it was not edited again after the fix.
- **Resumable batches.** Scans and fixes run in small batches, so large sites and short PHP time limits are fine.
- **Protected options.** `siteurl`, `home`, cron, rewrite rules and transients are never changed.

#### WP-CLI

- `wp trazelio scan` – scan and list findings.
- `wp trazelio fix "<id>" --dry-run` – count what would change.
- `wp trazelio fix "<id>"` – apply the fix.
- `wp trazelio rollback <run>` – roll a fix back.

#### Privacy

Trazelio does not send any data anywhere, does not call external services, has no tracking and needs no account. Everything happens in your own database.

## Requirements

- WordPress 6.2 or higher
- Tested up to WordPress 7.1.4
- PHP 7.4 or higher

## How to install

1. In your WordPress dashboard go to **Plugins → Add New Plugin**.
2. Search for **Trazelio**.
3. Click **Install Now**, then **Activate**.

Or download it directly from **[WordPress.org](https://wordpress.org/plugins/trazelio-migration-leftover-url-scanner/)**.

## Support

Questions or problems? Please use the **[support forum on WordPress.org](https://wordpress.org/support/plugin/trazelio-migration-leftover-url-scanner/)**.

## Author

Developed by **[Muhammad Mujahid Sarfraz](https://profiles.wordpress.org/mujahidwp/)** · [All my WordPress products](https://profiles.wordpress.org/mujahidwp/) · [LinkedIn](https://www.linkedin.com/in/muhammad-mujahid-sarfraz-2631a43b6)
