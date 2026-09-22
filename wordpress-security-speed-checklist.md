# WordPress Security & Speed Checklist

A practical checklist we run through when auditing a WordPress site for a small or medium-sized business. Nothing exotic here — just the basics people skip.

## Security

- [ ] **Keep WordPress core, theme, and plugins updated.** Most WordPress compromises exploit a known, already-patched vulnerability.
- [ ] **Remove unused plugins and themes entirely** — don't just deactivate them. Inactive code can still be exploited.
- [ ] **Use strong, unique passwords + limit login attempts.** A plugin like Limit Login Attempts Reloaded (or equivalent) stops brute-force attacks.
- [ ] **Disable file editing from the WP admin.** Add `define('DISALLOW_FILE_EDIT', true);` to `wp-config.php`.
- [ ] **Rename or protect the login URL** if the site gets automated login attempts (optional, but reduces log noise and load).
- [ ] **Set correct file permissions** — typically 644 for files, 755 for directories. Avoid 777.
- [ ] **Enforce HTTPS everywhere**, including internal links and asset URLs (mixed content warnings hurt both security and SEO).
- [ ] **Take automated off-site backups** (not just a local backup plugin) — daily for active sites, weekly minimum otherwise.
- [ ] **Use a security plugin for basic firewall + malware scanning** (Wordfence, Sucuri, or similar) if there's no server-level WAF.
- [ ] **Review user roles.** Remove old freelancer/agency admin accounts after a project ends.
- [ ] **Check `wp-config.php` isn't publicly accessible** and that directory listing is disabled on the server.

## Speed

- [ ] **Run a baseline PageSpeed Insights / Core Web Vitals check** before making changes, so you can measure impact.
- [ ] **Compress and serve images in WebP/AVIF**, and lazy-load below-the-fold images.
- [ ] **Enable page caching** (WP Rocket, W3 Total Cache, or a host-level cache) — this alone often has the biggest impact.
- [ ] **Minify and combine CSS/JS carefully** — test after combining, since aggressive minification can break Elementor widgets.
- [ ] **Use a CDN** for static assets if visitors are geographically spread out.
- [ ] **Audit installed plugins for load impact.** A query monitor plugin will show which plugins slow down each page load.
- [ ] **Set explicit width/height on images and embeds** to avoid layout shift (CLS).
- [ ] **Limit web fonts** to what's actually used — every extra font weight/style is a render-blocking request.
- [ ] **Clean up the database** periodically (post revisions, spam comments, expired transients) — a bloated database slows down every query.
- [ ] **Check hosting is appropriate for the traffic.** No amount of optimization fixes underpowered shared hosting for a growing site.

## Quick wins (do these first)

1. Update everything.
2. Turn on page caching.
3. Compress images site-wide.
4. Remove unused plugins/themes.
5. Re-run PageSpeed Insights and compare.

---

Maintained by [Onur Freelance](https://onurfreelance.com) — WordPress & Elementor web design, Maltepe/Istanbul.
