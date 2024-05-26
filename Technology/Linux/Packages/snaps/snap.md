#linux 
Tool to interact with snaps
[snap-getting-started](https://snapcraft.io/docs/getting-started), [quick start tour](https://snapcraft.io/docs/quickstart-tour).

Snaps are:
- auto-updated
- containerized in their own [[filesystem]].
- have  [channels](https://snapcraft.io/docs/channels).
- The snap server is not open source. You have to use [Canonical](https://en.wikipedia.org/wiki/Canonical_(company))'s snap store.
- very slow to open on the 1st start after boot.
- every snap mounts its [[filesystem]] as a disk drive. `lsblk`
- generally don't support system's theme.
## Info
List all commands: `snap help --all`
List installed snaps:   `snap list`
List all versions of specific snap: `snap list pycharm-community --all`
- `--all` list all versions still present in the */var/lib/snapd/snaps*
Info about a snap: `snap info <snap_name>`
Find a snap: `snap find <snap_name>`
Show current [[model-assertion]]: `snap known model`
Active model assertion information for this device: `snap model`

## Installation
Snaps are installed into: */var/lib/snapd/snaps*
**install** a snap:   `sudo snap install pycharm-community --classic`
- `--strict`   Default mode. Snaps run in complete isolation, up to a minimal access level that’s deemed always safe. Consequently, strictly confined snaps can not access your files, network, processes or any other system resource without requesting specific access via an interface
- `--classic`   Put snap in classic mode and disable security confinement.
- `--devmode`   A _devmode_ snap runs as a strictly confined snap with full access to system resources, and produces debug output to identify unspecified interfaces.
- `--channel=edge` install from the *edge* [channel](https://snapcraft.io/docs/channels).

Switch snap to a different channel: `sudo snap switch --channel=stable <snap_name>`

Remove a snap: `snap remove <snap_name>`, this will create a [snapshot](https://snapcraft.io/docs/snapshots) (except on [[Ubuntu-core]]) of the removed snap and retain it for 31 days.
	`--purge` will remove the snap without generating a snapshot. See [doc](https://snapcraft.io/docs/quickstart-tour#remove-a-snap-14).
### Updates
Manually check for updates: `snap refresh <snap_name>`
	Snaps are updated automatically. The above will check the [channel](https://snapcraft.io/docs/channels) being tracked by the snap.
Changing the channel being tracked and refreshing the snap can be accomplished with a single command: `sudo snap refresh --channel=beta vlc`
Updates are automatically installed within 6 hours of a revision being made to a tracked channel, keeping most systems up-to-date. This schedule can be tuned via configuration options and disabled with the `--hold` option.
Suspend updatiing: `snap refresh --hold=<duration> <snap1> <snap2>...`
	If not specified, `<duration>` defaults to forever.
	Example
```
$ snap refresh --hold=24h firefox
General refreshes of "firefox" held until 2023-10-26T14:10:53+01:00
```

[Downgrade](https://askubuntu.com/a/1225257)(revert) a snap to previous revision:`sudo snap revert pycharm-community`
Downgrade a snap to specific revision:`sudo snap revert pycharm-community --revision 212`
Refer to [Managing updates](https://snapcraft.io/docs/managing-updates) for more details.

## Configuration
Prints snap configurations: `snap get ubuntu-frame`
Change snap configuration: `snap set wpe-webkit-mir-kiosk url=https://ubuntu.com/core`, this will set the url to display to ubuntu.com/com/core.

## Permissions
Lists connections between plugs and slots in the system: `snap connections [snap_name]`
Connect an interface: `snap connect vlc:camera`

## Daemons
Display services: `snap services <snap>`. leave `<snap>` blank to list all.

## History
See details about changes during last update: `snap changes`, [doc](https://snapcraft.io/docs/managing-updates#monitor-changes-11).

## Development
Run a snap: `snap run <snap_name>`
	Links to snapped applications are located in */snap/bin* which is added to the system *$PATH*.
	
## More details
See [[snapcraft]] for creating a snap.
[data location](https://snapcraft.io/docs/quickstart-tour#where-snaps-store-data-12), and more details [here](https://snapcraft.io/docs/data-locations).
[snapshots](https://snapcraft.io/docs/snapshots).

