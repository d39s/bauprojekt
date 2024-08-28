# referenzen

This directory is synced from nextcloud.
Grab the required files and place them here once for local development.
DO NOT check in images here.

```
rclone sync --stats 1s --stats-one-line-date-format '' --stats-log-level NOTICE --stats-one-line "d39s:/Anpassung Referenzen/" src/assets/referenzen/ --include '/{{referenz-\d+/[^/]+\.(json|jpg|png)}}'
```

If you use rclone's `--delete-excluded` flag, make sure to un-delete `.gitignore` and `README.md` in this folder before committing, as rclone will have deleted those.
