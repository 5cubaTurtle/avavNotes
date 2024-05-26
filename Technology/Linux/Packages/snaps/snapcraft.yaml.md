Snaps are created using a build recipe defined in a file called *snapcraft.yaml*.
You can create the `snapcraft.yaml` file manually, or you can run the `snapcraft init` command to create a template file in the `snap` subdirectory.
A generated template file contains just enough data to build, split across three stanzas:
- Metadata.
- Confinement level.
- Build definition.

Mandatory declarations in a *snapcraft.yaml* file:
- **Metadata** - describes the snap functionality and provides identifiers by which the snap can be cataloged and searched in the Snap Store.
- **Security confinement** - describes the level of security of the snap.
- **Base** - describes which set of libraries the snap will use for its functionality. The base also defines the operating system version for the snap build instance in the virtual machine or container launched by Snapcraft. For instance, base: core18 means that Snapcraft will launch an Ubuntu 18.04 virtual machine or container, the set of tools and libraries used inside the snap will originate from the Ubuntu 18.04 repository archives, and the snap applications will “think” they are running on top of an Ubuntu 18.04 system, regardless of what the actual underlying Linux distribution is.
- **Parts** - describes the components that will be used to assemble the snap.
- **Apps** - describes the applications and their commands that can be run in an installed snap.

- A snap may contain one or more parts.
- A snap may contain one or more applications
- Parts can be pre-assembled binaries or they may be compiled as part of the build process.
- The parts section of the `snapcraft.yaml` file uses Snapcraft build system or language-specific plugins to simplify the build process.
- The parts section may also include a list of [build packages](https://snapcraft.io/docs/build-and-staging-dependencies) (build-packages) that will be used to create the snap applications but will not be included in the final snap. For instance, [[gcc]] or [[Makefile|make]].

## Mandatory metadata
- **Name** - A string that defines the name of the snap. It must start with an ASCII character and can only use ASCII lowercase letters, numbers and hyphens. It must be between 1 and 40 characters in length. The name must be unique in the Snap Store.
- **Version** - A string that defines the version of the application to the user. Max. length is 32 characters.
- **Summary** - A string that briefly describes the application. The summary can not exceed 79 characters. You can use a chevron ‘>’ character in this key to declare a multi-line summary.
- **Description** - A string that describes the application. You can use multiple lines. There is no practical limitation on the length of this key.

This metadata will be used to pre-populate certain fields in the snap’s Snap Store page.
