
# ImageJ/Prairie Reader Plugin

## Default Installation (Install ImageJ version 1.49 with Prairie Reader Plugin)
1. Extract the ImageJ archive (the .zip file accompanying this document) to **C:\Program Files**.
Another location can be used if desired, for example the Windows Desktop. Note that all of the individual plugins/macros which needed to be copied manually in previous versions are now already included in the correct folders within the archive
2. (Optional) Create one of more shortcuts to **ImageJ.exe**. If extracted to the Program Files folder in step 1 the path to the executable will be **C:\Program Files\ImageJ\ImageJ.exe**. To create a shortcut right click on the executable and select the **Create shortcut** option, from there the shortcut can be renamed and moved to another location; for example, the Windows Desktop
3. To run ImageJ use the shortcut(s) created in step 2, or run the executable mentioned in step 2 directly

## Custom Installation (Add/Update Prairie Reader in existing ImageJ/Fiji installation)
1. Find the folder for the ImageJ/Fiji installation; if there is a shortcut right click on it and select **Properties**, then click the **Open File Location** button
2. Copy **Prairie_Reader.jar** to the **…\plugins\Input-Output** folder
3. Copy **PVReader.txt** to the **…\macros** folder (required to open Prairie View data sets from the command line/actions, but otherwise optional)
4. Restart ImageJ/Fiji if it was already running for the plugin to become available

## Measuring Point Spread Functions
To use the EPFL PSF function, on the ImageJ menu select **Plugins -> MetroloJ -> Generate PSF Report**.  Note that to use this option it is necessary to crop the image for a single bead; from the ImageJ menu **Image -> Crop** and then drag a region around a bead.

## Using the Prairie Reader Plugin
1. Start ImageJ (step 3 of the installation instructions above)
2. On the ImageJ menu bar select **Plugins -> Input-Output -> Prairie Reader** to bring up the **Prairie Reader** dialog
3. At the bottom right of the **Prairie Reader** dialog click the **Load Image(s)...** button and select a .xml metadata file from a Prairie View data set to open. The metadata associated with that data set will be displayed on the **Prairie Reader** dialog and one or more image windows will be opened to display the currently selected image sequence; one image window for each individual channel and one image window with a composite view of all channels (if more than one channel of data is present)

## Automatically Loading Images in ImageJ from Prairie View
An **After Scan Complete/Playback** action can be configured in Prairie View to either load a data set in ImageJ from playback mode, or automatically load a data set in ImageJ instead of (or in addition to) playback mode

To set up and use the **After Scan Complete/Playback** action:
1. From the main menu in Prairie View select **Tools -> Actions...**
2. On the first tab (already visible) at the bottom, press the **New** button in the **After Scan Complete/Playback** section
3. Enter a **Name** for the action in the text box to the right, for example **Open in ImageJ**
4. Below that click the **...** (ellipses) button for the **Filename** and select the ImageJ executable mentioned above in step 2 of the installation instructions
5. Below that in the **Arguments** field enter **-port1 -macro "PVReader" "&lt;metadata&gt;"**
6. Click the **Accept** button in the lower right to save the changes and close the **Actions** dialog
7. In playback mode it is now possible to select the **Open in ImageJ** action from the **Actions** dropdown on the **Playback Controls** dialog and press the **Perform** button to the right to open the data set in ImageJ
8. (Optional) On the **Misc** tab of the main control window the **Open in ImageJ** script can be selected for the **After Scan** dropdown in the **Actions to Perform** section to automatically open a data set in ImageJ after it is acquired. To stop opening datasets in playback mode deselect **Automatically Start Playback After Acquisition** from the **Preferences** menu
9. (Advanced/Optional) Following steps 1-3 again (using a different name) select the **Rule** option instead of **Action**, and select one or more **Scan Types** to run the **Open in ImageJ** action already created, to only open specific types of data sets in ImageJ when selected in step 8

## Making Changes/Recompiling Prairie Reader Plugin
This is a legacy plugin that has been compiled using just ImageJ 1.49, as a result the compilation process isn't very straightforward:
1. For some reason, perhaps an ImageJ bug that has since been fixed, attempting to compile plugin code for a plugin which is already installed doesn't work, so the Prairie_Reader.jar file must be removed from the plugins folder (or file extension changed to .ignore ore something ImageJ won't try and load) prior to compilation.
2. To make file management easier Prairie_Reader.java should be in it's own folder.  This is where ImageJ will stick all the .class files and they are easier to compress into a .zip/.jar file if there aren't other files in the same folder.
3. Run ImageJ and from the menu select **Plugins** -> **Macros** -> **Edit...**
4. Select Prairie_Reader.java from wherever the source file is located and click open.
5. It is possible to make changes to the source file and save them if that hasn't been done already.
6. From the editor dialog menu select **File** -> **Compile and Run**
7. There will be an error message that the Prairie_Reader class could not be found, but the .class files will have been compiled if there were no syntax issues.  There is no indication of compiler errors aside from no .class files being generated.
8. Select all files in the folder and add then to a .zip file. It's ok to include the .jaja file as well, and encouraged so it is available as a reference.
9. Rename the zip file to **Prairie_Reader.jar**
10. Move or copy the newly created  **Prairie_Reader.jar** file to the ImageJ plugins folder and restart ImageJ to use it.
