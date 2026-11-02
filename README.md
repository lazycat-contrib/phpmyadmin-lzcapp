# phpMyAdmin (LazyCat LPK)

Web interface for MySQL / MariaDB, bundled with a database server.

- Upstream: https://github.com/phpmyadmin/phpmyadmin
- Image: `library/phpmyadmin:5.2.3` (official Docker Hub image, mirror mode, digest-matched)
- License: GPL-2.0 (full text in `content/licenses/LICENSE`)
- Containers: phpMyAdmin + MariaDB 10.11

## Notes

- Standalone phpMyAdmin is useless without a server to connect to, so this package bundles
  MariaDB and points `PMA_HOST` at it. A ready-made empty database `appdb` is created.
- The root password is a **deploy param** (`$random(len=20)` by default), shared by both the
  bundled database and the phpMyAdmin login, so there is no built-in credential.
- `PMA_ABSOLUTE_URI` is set to the app domain so redirects and assets resolve correctly
  behind the LazyCat entry proxy.
- `UPLOAD_LIMIT=256M` to make SQL imports practical.
- Data on `/lzcapp/var/{db,sessions}`.
- Not yet verified on a real device.
