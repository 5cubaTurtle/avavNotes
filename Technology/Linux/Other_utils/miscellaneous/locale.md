Get locale-specific information
[SO answer](https://unix.stackexchange.com/a/87763)

Print locale variables: `locale`

### `LC_ALL=C`
You generally run a command with `LC_ALL=C` to avoid the user's settings to interfere with your script.
In a script, if you want to force a specific setting, as you don't know what settings the user has forced (possibly `LC_ALL` as well), your best, safest and generally only option is to force `LC_ALL`.
The `C` locale is a special locale that is meant to be the simplest locale.
