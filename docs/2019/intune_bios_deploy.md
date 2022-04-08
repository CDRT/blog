## Deploying ThinkPad BIOS Updates With Intune
*Author: Philip Jorgensen*

This walk-through will cover deploying ThinkPad BIOS updates with Intune. These are provided as standalone executables so adding them as a Win32 client app will involve converting them to the .intunewin format using the [Win32 Content Prep Tool](https://github.com/Microsoft/Microsoft-Win32-Content-Prep-Tool). 

### App Conversion
Create a working folder where the Win32 App Packaging Tool and BIOS packages will reside. Download the latest BIOS for your model system and save it to a working folder. In a PowerShell or Command Prompt, run the **IntuneWinAppUtil.exe** and follow the prompts to:

- Specify the source folder - This is the location where the BIOS package downloaded from the web is saved.
- Setup File - The BIOS package file name, i.e. **r0suj16w.exe**
- Output folder - Location where the converted app will drop.   

Once this information is entered, you will see the tool validate the package parameters, encrypt the content, and generate the detection XML file.  You'll now have a new file in the .intunewin format, which will need to be uploaded into Intune.

### Add the Win32 App
Login to Intune and navigate to Client Apps > Apps  and click the Add button to add a new app.  You'll need to choose Windows app (Win32) from the list