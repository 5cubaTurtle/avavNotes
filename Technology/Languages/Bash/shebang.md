Shebangs is placed at the top of the script. It specify the interpreter to use for executing the script. 
### `#!/usr/bin/env bash` vs. `#!/bin/bash`
`#!/usr/bin/env bash` uses the `env` utility to locate the *Bash* interpreter in the system's `$PATH`. This allows the script to be executed by any user who has *Bash* installed in their system, regardless of where *Bash* is located. This makes the script more portable across different systems and distributions.

`#!/bin/bash`, on the other hand, specifies the absolute path to the *Bash* interpreter. This assumes that *Bash* is always installed in the same location on every system, which is not always the case.

For python scripts use `#!/usr/bin/env python3`
