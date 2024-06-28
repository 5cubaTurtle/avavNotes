search the manual page names and descriptions

Each manual page has a short description available within it.  apropos searches the descriptions for instances of *keyword*.

*keyword*  is  usually a regular expression, as if (-r) was used, or may contain wildcards (-w), or match the exact keyword (-e).  Using these options, it may be necessary to quote the keyword or escape (\\) the special characters to stop the shell from interpreting them.
