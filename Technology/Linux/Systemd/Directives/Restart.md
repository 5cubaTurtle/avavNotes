`Restart=` specifies the conditions under which a service should be automatically restarted if it exits.

Possible values for `Restart=`:
-   `no` (default): The service will not be restarted automatically.
-   `on-success`: The service will be restarted automatically only if it exits with a status code of 0, indicating success.
-   `on-failure`: The service will be restarted automatically if it exits with a non-zero status code, indicating failure.
-   `on-abnormal`: The service will be restarted automatically if it exits abnormally (i.e., with a signal or an unexpected error).
-   `on-abort`: The service will be restarted automatically if it exits due to an abort signal.
-   `on-watchdog`: The service will be restarted automatically if it fails to ping its watchdog process in time.
-   `always`: The service will be restarted automatically regardless of the exit status.

By default, if the `Restart=` directive is not specified, the value is set to `no`, which means that the service will not be automatically restarted if it exits.
You can set the `Restart=` directive in the `[Service]` [[#Sections|section]] of a [[systemd]] service unit.