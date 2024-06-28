To display images from a Raspberry Pi 5 over SSH on your desktop Ubuntu machine, you have several options. Here are the most commonly used methods:

### 1. X11 Forwarding
X11 forwarding allows you to run graphical applications on the Raspberry Pi and display them on your desktop. To use X11 forwarding:

1. **Ensure `ssh` and `xauth` are installed:**
   On your Raspberry Pi, install the necessary packages:
   ```bash
   sudo apt-get update
   sudo apt-get install xauth
   ```

2. **Enable X11 forwarding in your SSH configuration:**
   On your desktop, edit the SSH configuration file (`/etc/ssh/ssh_config` or `~/.ssh/config`) to include the following line:
   ```bash
   ForwardX11 yes
   ```

3. **Connect to the Raspberry Pi with X11 forwarding:**
   Open a terminal on your desktop and connect to the Raspberry Pi with the `-X` or `-Y` option (for me, connecting regularly, i.e. w/o `-X` works when using [[feh]])
   ```bash
   ssh -X pi@raspberrypi.local
   ```

4. **Display an image:**
   Use an image viewer like `feh` or `eog` on the Raspberry Pi:
   ```bash
   feh image.png
   ```
   The image should be displayed on your desktop.

### 2. Using `scp` to Transfer Images
If you prefer to transfer the image files to your desktop and view them locally, you can use `scp`:

1. **Transfer the image:**
   ```bash
   scp pi@raspberrypi.local:/path/to/image.png /local/path/to/save/
   ```

2. **View the image on your desktop:**
   Use your preferred image viewer to open the file:
   ```bash
   eog /local/path/to/save/image.png
   ```

### 3. Using VNC
VNC allows you to access the entire Raspberry Pi desktop environment remotely:

1. **Install VNC server on the Raspberry Pi:**
   ```bash
   sudo apt-get update
   sudo apt-get install realvnc-vnc-server
   ```

2. **Enable VNC on the Raspberry Pi:**
   ```bash
   sudo raspi-config
   ```
   Navigate to `Interfacing Options` > `VNC` and enable it.

3. **Install a VNC viewer on your desktop:**
   For Ubuntu, you can use `Remmina`:
   ```bash
   sudo apt-get install remmina
   ```

4. **Connect to the Raspberry Pi:**
   Open Remmina, create a new VNC connection, and enter the Raspberry Pi’s IP address. Once connected, you can interact with the Raspberry Pi’s desktop and open images as needed.

### 4. Using `SFTP` with an Image Viewer
Some image viewers support opening files directly from remote servers using SFTP:

1. **Install an image viewer with SFTP support:**
   For example, `gthumb` supports this feature:
   ```bash
   sudo apt-get install gthumb
   ```

2. **Open the image using SFTP:**
   In `gthumb`, you can open an image using the `File` > `Open Location` menu and entering the SFTP URL:
   ```
   sftp://pi@raspberrypi.local/path/to/image.png
   ```

These methods should allow you to view images from your Raspberry Pi 5 on your Ubuntu desktop over SSH effectively. Choose the method that best fits your workflow and requirements.