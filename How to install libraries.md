Arduino libraries are collections of code that are designed to provide additional, reusable functionality or to simplify using external electronic modules.

Libraries typically come with examples of how to use them. The library developer usually provides online documentation and explains how it possibly relates to what you are trying to achieve.

## Installing a library
There are three different ways to install libraries; we'll show you each of them.

### Arduino Library Manager
The simplest method of installing libraries is using the Library Manager built into the Arduino IDE.

You can access the Library Manager from the menu bar:
*Sketch - Include Library - Manage Libraries...*

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/5ea905fb-dbc4-48be-ad8e-8351c26cfad2)


A new window will open:
![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/fbec804e-4549-4c8b-a66b-12587b9175ac)


From here you can search for libraries to use in your code. Only a few libraries are currently available this way, as this feature is relatively new. You will often have to manually download and install a library, following the other two processes.

### ZIP library
Locate and download a library you wish to use. Sometimes the library will download as a `*.zip` archive, which can sometimes be installed directly without restarting the Arduino IDE.

Similar to the Library Manager, this option is in the menu bar:
*Sketch - Include Library - Add .ZIP Library...*
![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/c39d7f71-5d73-465a-a8af-3e8aca68b0bb)


Use the file dialog to locate and select the zip file from your Downloads folder. You will be notified if the installation has been successful – otherwise you'll need to install manually.

### Manually adding libraries
This is the original method of adding libraries.

1. Locate the `Arduino` folder inside your `Documents` directory.
1. Open the `libraries` folder. If not found, create a new folder with that name (must be lowercase).
1. Unzip the library archive that you wish to install.
1. Inside the archive you should find a folder bearing the name of the library – for example 'MPR121'.
1. Copy this entire folder (named 'MPR121' in our example) into the Arduino's `libraries` folder.
1. Restart the Arduino IDE.
1. In the menu bar, select `Sketch` > `Include Library`. You should now see that your library is listed.
