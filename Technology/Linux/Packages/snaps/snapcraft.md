Package, distribute, and update snaps for Linux and IoT.

[docs](https://snapcraft.io/docs/snapcraft), `snapcraft help --all`
[basic snapcraft example](https://snapcraft.io/docs/snapcraft-basic-example), [intermediate example](https://snapcraft.io/docs/snapcraft-intermediate-example).

Uses the file [[snapcraft.yaml]].

Install snapcraft: ` sudo snap install snapcraft --classic`
Create a key and store it locally: `snapcraft create-key <key-name>`
Initialize a snapcraft project in the current directory: `snapcraft init`

## Build lifecycle
Snaps are [built](https://snapcraft.io/docs/parts-lifecycle) in several steps, collectively known as the “lifecycle”:
- **Pull** - At this step of the snap build process, Snapcraft downloads or retrieves the components needed to build the relevant part. For instance, if source points to a Git repository, the pull step will clone that repository.
- **Build** - Snapcraft constructs the part from the previously pulled components. Since the snap ecosystem supports multiple types of applications (C, Java, Go, Rust, Python, etc.), the build definition also needs to include a specification on how to construct the part. This is done by declaring a [Snapcraft plugin](https://snapcraft.io/docs/snapcraft-plugins). Parts are processed linearly, unless there is a dependency order declared.
- **Stage** - Snapcraft copies the built parts into the staging area. Parts are not ordered at this point, and there might be an additional level of processing to ensure the snap contains the required files, and that there are no conflicts between parts. This is an advanced topic beyond the scope of this tutorial.
- **Prime** - Snapcraft copies the staged components into the priming area, where the files will be placed in their final locations (folder and files path hierarchy) for the resulting snap. The prime step is similar to the stage step, but it may exclude certain components from the stage step.
- **Pack** - Snapcraft packs the assembled components in the prime directory into a single archive.

The artifact of a successful Snapcraft build run is a snap file, which is itself a compressed [[mksquashfs|squashfs]] archive distinguished by the .snap suffix.

[plugins](https://snapcraft.io/docs/snapcraft-plugins)

### Creating a snap
1. create a folder for the snap and initialize it:
```shell
mkdir asciinema
cd asciinema
snapcraft init
```
2. edit the .yaml file: