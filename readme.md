# Jetraw Micro-Manager, the Jetraw and Dpcore plug-ins for Micro-Manager. 
This is the public repository for **Jetraw and DPcore plug-ins** compatible with Micro-Manager. With both plug-ins the user is able to **Dpcore prepare the acquired images** and then optionally the user can **compress the images using Jetraw** within Micro-Manager.  
<br/>For more info visit:
https://www.jetraw.com/

## Requirements
- **Jetraw installed** on a Windows computer (MacOS and Linux coming soon) and installation folder must be in PATH environment variable.<br/>
*Note:* if you do not have Jetraw installed visit https://www.jetraw.com/downloads/software and for usage information https://github.com/Jetraw/Jetraw  

- **Micro-Manager 2.0 installed** for Windows 64 bits.<br/>
*Note:* if you do not have Micro-Manager installed visit https://micro-manager.org/Download_Micro-Manager_Latest_Release

- For writing compressed files a **valid License** is needed. 

At the moment **only PCO cameras are supported** and **Hamamatsu cameras** will be supported soon. Remember as well that **only 16-bit images** are supported. If you want to integrate/calibrate any other type of camera please [contact us.](#Contact)

**PCO cameras** can also use the PCO Generic Adapter that is provided within the **Micro-Manager 1.4**. PCO has already integrated the Dpcore plug-in module into its software, therefore if Micro-Manager detects a valid Jetraw installation the user will be able to Dpcore prepare the acquired image.  
  
For more information contact PCO or directly explore the source code available at:    
https://github.com/micro-manager/micro-manager/tree/svn-mirror/DeviceAdapters/PCO_Generic

## Installation
You will need the following JAR files for installation:

- **MMJ_** jar file. 
- **DpcorePlugin** jar file.
- **JetrawSaverPlugin** jar file.

Download the ZIP file that contains all necessary JAR files from [latest (pre-)release](https://github.com/Jetraw/MicroManager/releases/download/21.07.01.1/Jetraw_MicroManager_21.07.01.1.zip).
  
If you need a previous version please go to [previous versions.](https://github.com/Jetraw/MicroManager/releases/)

**Replace MMJ_.jar** in your MicroManager folder:<br/>
path_to_micromanager\plugins\Micro-Manager\

**Copy/replace your .jar plug-ins files** (DpcorePlugin.jar and JetrawSaverPlugin.jar) into:<br/>
path_to_micromanager\mmplugins\

*Note:* Micro-Manager only accepts one version of each plug-in. Therefore if a previous version of the plug-in is present in the folder, it must be removed. 

## Usage
Once all .jar files have been replaced/copied, you should be able to Dpcore prepare an acquired image and save a Jetraw compressed version of it during acquisition.  

In MicroManager you need to modify the internal image processing pipeline introducing Dpcore and Jetraw processes using the **Micro-Manager plug-in *On-the-fly Image Processing***.<br/>
  
Once the processing pipeline dialog is opened **select Dpcore Plug-in** and **Jetraw Saver** in this order. **(Note: IMPORTANT order matters).**

Your processing pipeline configuration should look as follows:

![alt text](https://github.com/Jetraw/MicroManager/blob/master/screenshots/pipeline_configuration.png)

*1. Micro-Manager pipeline configuration*

In the configuration section of the **DPcore plug-in** you can **choose the camera** and the **camera identifier** to be used with dpcore. Only the registered identifiers for the specific camera will appear in the drop-down menu. 

![alt text](https://github.com/Jetraw/MicroManager/blob/master/screenshots/dpcore_plugin.png)

*2. Dpcore plug-in configuration*

In the configuration section of the **Jetraw Saver plug-in** you can **choose the output folder** for your compressed images.

![alt text](https://github.com/Jetraw/MicroManager/blob/master/screenshots/jetraw_saver_plugin.png)

*3. Jetraw saver plug-in configuration*

Then you are **ready to do an acquisition** which prepares the images and saves a compressed copy of it. To proceed with the acquisition please **press the icon "Multi-D Acq."** in the main Micro-Manager panel.  
  
**IMPORTANT:** remember that while having Jetraw compression active the **Live and Snap options** will not work properly as a compressed image is not directly displayable, therefore **if you want preview your camera the Jetraw Saver Plugin must be removed from the processing pipeline or disable the Snap/Live option.** Our development team is already exploring alternatives to remove this limitation. 

![alt text](https://github.com/Jetraw/MicroManager/blob/master/screenshots/acquisition_screen.png)

*3. Acquisition of 40 frames, 20 time points and 2 slices*

**After the acquisition** is performed, if you have used the Jetraw Saver Plug-in, a Jetraw compressed TIFF file will be located at the folder you previously indicated. You have two options to **display this compressed image:**

- Decompress the image using Jetraw's UI or command line tool, and display the decompressed image using ImageJ/Fiji or MicroManager, all options are capable of reading the dimensional and time coordinates generated by the acquisition.

- Display directly the compressed image using Jetraw's Native Fiji Plug-in or Jetraw's Bio-Formats Plug-in. The Fiji Native plug-in does not have the option to read the different dimensional and time coordinates from MicroManager???s acquisition at the moment, it just displays the whole amount of frames from the TIFF file. You can find the plug-ins in our website: https://www.jetraw.com/downloads/software

## Contact
Feel free to use the [issues section](https://github.com/Jetraw/MicroManager/issues) to report bugs or request new features. You can also ask questions and give comments by visiting the [discussions](https://github.com/Jetraw/MicroManager/discussions), or following the contact information at https://jetraw.com.
