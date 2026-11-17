# TestGentry

A Fourge CMS site, installed from [YourDigitalGroup/FoundryCMS](https://github.com/YourDigitalGroup/FoundryCMS) at engine version 1.14.159.

## Deploy

Every push to `main` deploys to the server over FTP (`.github/workflows/deploy.yml`). The workflow needs these four repository secrets (Settings → Secrets and variables → Actions):

- `FTP_SERVER`
- `FTP_USERNAME`
- `FTP_PASSWORD`
- `FTP_SERVER_DIR`

## Server setup

1. Copy `admin/config.secret.example.php` to `admin/config.secret.php` **on the server** and set `db_secret_key` to a long random string (`php -r "echo bin2hex(random_bytes(32)).PHP_EOL;"`). Never commit that file; it is gitignored.
2. Sign in at `/admin/` with your usual 44i Fourge account. The first sign-in seeds the accounts database (`admin/fourge.db`) from `data/users.json`, which carries the same team accounts as every other Fourge site.

## Pages

The site starts with no public pages. Build them in the CMS, or bring them in with **Site Foundry → Import from Server / Import ZIP**.

## Engine updates

The CMS updates its own engine files from FoundryCMS when someone signs in. Don't edit the engine files here (`admin/index.html`, `admin/api.php`, `admin/db.php`, `block-renderer.jsx`, `blog-post.jsx`, `interior-shell.jsx`, `posts.jsx`, `preview.html`, `adaptify.js`, `fourge-chat.js`): the next update overwrites them. Make engine changes in FoundryCMS instead.
