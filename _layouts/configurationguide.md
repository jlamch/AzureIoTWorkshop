---
layout: default
---
<section class="hero diagonal">
	<div class="container">

	
	</div>
</section>

<section class="diagonal">
	<div class="text-container">
		
## Prepare the development environment

We recommend [Azure IoT Tools](https://aka.ms/azure-iot-tools) extension pack for Visual Studio Code to develop on the DevKit. The Azure IoT Tools contains [Azure IoT Device Workbench](https://aka.ms/iot-workbench) to develop and debug on various IoT devkit devices and [Azure IoT Hub Toolkit](https://aka.ms/iot-toolkit) to manage and interact with Azure IoT Hub.

You can watch these [Channel 9](https://channel9.msdn.com/) videos to have overview about what they do:

* [Introduction to the new IoT Workbench extension for VS Code](https://channel9.msdn.com/Shows/Internet-of-Things-Show/IoT-Workbench-extension-for-VS-Code)
* [What's new in the IoT Toolkit extension for VS Code](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Whats-new-in-the-IoT-Toolkit-extension-for-VS-Code)

Follow these steps to prepare the development environment for DevKit:

1. Install [Arduino IDE](https://www.arduino.cc/download_handler.php?f=/arduino-1.8.12-windows.exe). It provides the necessary toolchain for compiling and uploading Arduino code.
    * **Windows**: Use Windows Installer version. Do not install from the app store.
    * **macOS**: Drag and drop the extracted **Arduino.app** into `/Applications` folder.
    * **Ubuntu**: Unzip it into folder such as `$HOME/Downloads/arduino-1.8.8`

2. Install [Visual Studio Code](https://code.visualstudio.com/), a cross platform source code editor with powerful developer tooling, like IntelliSense code completion and debugging.

3. Launch VS Code, look for **Arduino** in the extension marketplace and install it. This extension provides enhanced experiences for developing on Arduino platform.

    ![Install Arduino](https://github.com/Microsoft/azure-iot-developer-kit/blob/pre-release/docs/assets/images/getting-started/install-arduino.png?raw=true)

4. Look for **Azure IoT Tools** in the extension marketplace and install it.

    ![Install Azure IoT Tools](https://github.com/Microsoft/azure-iot-developer-kit/blob/pre-release/docs/assets/images/getting-started/install-azure-iot-tools.png?raw=true)

5. Configure VS Code with Arduino settings.

    In Visual Studio Code, click **File > Preference > Settings**.

    ![Open settings](https://github.com/Microsoft/azure-iot-developer-kit/blob/pre-release/docs/assets/images/getting-started/setting-1.png?raw=true)

    Type "Arduino" in the search textbox, the **Arduino:Additional Urls** is showed up, then click the hyperlink '**Edit in settings.json**'.

    ![Find settings](https://github.com/Microsoft/azure-iot-developer-kit/blob/pre-release/docs/assets/images/getting-started/setting-2.png?raw=true)

    Make sure the ```"arduino.path"``` and ```"arduino.additionalUrls"``` have been set correctly, if not please add following lines to configure Arduino depending on your platform:

    * **Windows**:

        ```json
        "arduino.path": "C:\\Program Files (x86)\\Arduino",
        "arduino.additionalUrls": "https://raw.githubusercontent.com/VSChina/azureiotdevkit_tools/master/package_azureboard_index.json"
        ```

    * **macOS**:

        ```json
        "arduino.path": "/Applications",
        "arduino.additionalUrls": "https://raw.githubusercontent.com/VSChina/azureiotdevkit_tools/master/package_azureboard_index.json"
        ```

    * **Ubuntu**:

        Replace the **{username}** placeholder below with your username.

        ```json
        "arduino.path": "/home/{username}/Downloads/arduino-1.8.8",
        "arduino.additionalUrls": "https://raw.githubusercontent.com/VSChina/azureiotdevkit_tools/master/package_azureboard_index.json"
        ```

6. Click `F1` to open the command palette, type and select **Arduino: Board Manager**. Search for **AZ3166** and install the latest version.

    ![Install DevKit SDK](https://github.com/Microsoft/azure-iot-developer-kit/blob/pre-release/docs/assets/images/getting-started/install-az3166-sdk.png?raw=true)

### Install ST-Link drivers

[ST-Link/V2](http://www.st.com/en/development-tools/st-link-v2.html) is the USB interface that IoT DevKit uses to communicate with your development machine. Follow the OS-specific steps to allow the machine access to your device.
<p class="editable">
<a href="{{ site.baseurl }}/images/en.stsw-link009.zip">ST Link driver for windows - my copy without signin</a></p>
		
* **Windows**: Download and install USB driver from [STMicroelectronics website](http://www.st.com/en/development-tools/stsw-link009.html).
* **macOS**: No driver is required for macOS.
* **Ubuntu**: Run the following in terminal and log out and log in for the group change to take effect:

    ```bash
    # Copy the default rules. This grants permission to the group 'plugdev'
    sudo cp ~/.arduino15/packages/AZ3166/tools/openocd/0.10.0/linux/contrib/60-openocd.rules /etc/udev/rules.d/
    sudo udevadm control --reload-rules

    # Add yourself to the group 'plugdev'
    # Logout and log back in for the group to take effect
    sudo usermod -a -G plugdev $(whoami)
    ```

Now you are all set with preparing and configuring your development environment. Let us build the “Hello World” sample for IoT: sending temperature telemetry data to Azure IoT Hub.

## Create your first project

1. Make sure your IoT DevKit is **not connected** to your computer. Start VS Code first, and then connect the DevKit to your computer.

1. Click `F1` \ `Shift+Ctrl+P` to open the command palette, type and select **Azure IoT Device Workbench: Create Project ...**.
Provide project name. Choose **Arduino** as Project base, then select **MXChip IoT DevKit** as template (only device code).

1. In the bottom-right status bar, check the **MXCHIP AZ3166** is shown as selected board and serial port with **STMicroelectronics** is used. If it is not listed **Refresh Pagckage Indexes**

    ![Select board and COM](https://github.com/Microsoft/azure-iot-developer-kit/blob/pre-release/docs/assets/images/getting-started/select-com.png?raw=true)

1. Click `F1` again, type and select **Azure IoT Device Workbench: Upload Device Code**. It starts compile and upload the code to DevKit. Or select **Arduino: Verify** for compile and **Arduino: Upload** to upload the code to DevKit.

	</div>
</section>
