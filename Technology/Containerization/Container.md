A container is a lightweight, standalone, executable package that includes everything needed to run a piece of software, including the code, runtime, system tools, system libraries, and settings. Containers isolate applications from each other and from the underlying infrastructure, making them portable and consistent across different environments.

Container is built using an [[Image]] and typically includes the following components:

1. **Application Code**: The code or executable files that make up the application to be run inside the container.
2. **Dependencies**: Any libraries, frameworks, or runtime environments required by the application to execute properly.
3. **Operating System Libraries**: Essential system libraries and binaries needed for the application to run, typically stripped down to only what is necessary to reduce image size.
4. **Configuration Settings**: Environment variables, configuration files, and settings necessary for the application to operate correctly.
