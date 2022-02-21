# **Contents**

### **Reading Wabbajack Logs**
  [Wabbajack Logs 101](#wabbajack-logs-101)

### **General Issues**
  [Wabbajack - General Issues](#general-wabbajack-issues)
  
  [Living Skyrim - General Issues](#general-living-skyrim-issues)
  
  [Path of the Dovahkiin - General Issues](#general-path-of-the-dovahkiin-issues)
  
  [MOISE - General Issues](#general-moise-issues)

### **Tempoarary Issues**
  [Wabbajack - Temporary Issues](#temporary-wabbajack-issues)

  [Living Skyrim - Temporary Issues](#temporary-living-skyrim-issues)

  [Path of the Dovahkiin - Temporary Issues](#temporary-path-of-the-dovahkiin-issues)



# Wabbajack Logs 101

**A brief explanation of the contents of a typical Wabbajack log.**

This will be an overview of the contents of a typical Wabbajack log file with each section roughly explained (at least to the best of my ability) and what type of information you can usually extract from each part of the log. I've included some screenshots to help.

Fully detailed solutions and things to look for in logs will be included in the General Issues section for quick reference.

![image](https://user-images.githubusercontent.com/38520983/154885616-de500839-1a38-4c07-8326-264054c214e9.png)

Here is the beginning of a log file. The first line shows you the Wabbajack build version, this is usually not needed for support issues.

The second line shows the current location wabbajack is running in. This can be useful in several different ways, chiefly, making sure Wabbajack isn't being run from any protected windows locations such as: The Desktop, Documents, Pictures, Downloads, etc. While sometimes this may not be an issue at all it is a good thing to check first and possibly make the user aware that you can run into errors with Wabbajack in any of these locations - Good advice to fix: have them run wabbajack from it's own folder `C:\Wabbajack` or similar.

The Third line shows the current Operating System version. Usually not an issue for support, but the general consensus is that running Wabbajack and by extention most modlists on anything prior to Windows 10 will lead to issues.

The next two lines show general system information such as the amount of RAM available as well as the display settings and video memory size, as well as a warning if the pagefile for the system is below 20000MB. While generally not useful for diagnosing Wabbajack issues it can be helpful to check and advise the user if their system specs seem especially low for the requirements of the list. Pagefile can be an issue if Wabbajack is reporting out of memory errors.

You may also see an entry around this point of the log saying: `Outside of standard install folder, not updating` This generally means the user is running wabbajack from inside the Version folder for wabbajack and not using the main launcher. While typically not a problem it can cause issues if the list requires a newer version of Wabbajack than the version they are currently running. Otherwise this line can generally be ignored.

![image](https://user-images.githubusercontent.com/38520983/154886587-399f8473-33d0-4c11-bb87-d9e780195baa.png)

The next section in a log is the Game Finder function. It will typically start with Steam games. If this section is completely missing it usually indicates Steam is not installed. (only really relevant for MOISE support currently).

In general you will see an entry in this section list the name of the game, the Steam APPID in brackets, then the path the game was found in the registry.

To go into detail we'll break down Skyrim Special Edition's entry as that's usually the most relevant:

![image](https://user-images.githubusercontent.com/38520983/154886910-333ee2ac-afdb-4433-8ddd-f91095b37da9.png)

The first thing to note is the path the game is found at. In this case it's `G:\SteamNVMe\steamapps\common\Skyrim Special Edition`
Legiitmate Steam game installs will always list the last part of the path as `steamapps\common\[game name here]` as long as the last part includes this part you can reasonably safely assume it is not a pirated copy. If the path is someting like: `F:\Games\Skyrim SE\` or is very similar to the official paths but the game name is different: `G:\SteamNVMe\steamapps\common\Skyrim SE` for example, chances are high it's a pirated copy of the game, and you should ask for a screenshot of their Skyrim Directory to make sure. (further details in the Piracy General Issues section)

Having the game installed in ProgramFiles is less of an issue with the Stock Game feature than it was previously, but it is still something to keep in mind if issues persist after other troubleshooting steps.

If an entry for the game required by the list isn't present that usually indicates either: 
* The game isn't installed at all
* The game hasn't been run once since being installed (usually required to set registry/config settings)
* Possibly pirated and as such isn't being found by Wabbajacks Game Finder.

You may occassionaly see double entries for games in the list of games. While this isn't generally considered an issue it's something to keep in mind if issues persist with the install and no other solutions are found.

And lastly if the game required *is* in the list but Wabbajack is still reporting it cannot find the game, that usually means the user either has multiple copies of the game installed or has moved the files manually and Steam is still assuming the game is in the previous location. It's good practice to double check where the user ~thinks~ the game is installed and compare it to where the log says it's looking for the game. This is usually caused by users cut/pasting the game files out of the installed folder to somewhere else, usually to move the install outside of Program Files.


![image](https://user-images.githubusercontent.com/38520983/154888204-02e1d077-5700-4674-9007-41d3567e8629.png)

The next section in a log will be the other Game Finder locations, such as Origin, Epic Game Store, GOG etc. This is currently only relevant for MOISE support, further information will be in MOISE general issues.


![image](https://user-images.githubusercontent.com/38520983/154889570-d4ac5e65-8b81-489e-8aa5-6aec636ec554.png)

Next we have lines showing the Wabbajack version. This should generally always be the latest version of Wabbajack, if an older version of Wabbajack is being used to install a list that was compiled on a newer version the list will not install and an error will be displayed on the screen where the user selects the install and download paths. 

Next are some entries showing the status of the Wabbajack build server. If this shows anything other than `Build Server is alive` this will usually indicate either an error on the users side or an error with the connection to the Wabbajack build server, unfortunately it's usually difficult to tell which. It would be best to check the wabbajack discord if this is an issue multiple users are having it can generally be assumed it's an issue on Wabbajacks side.

The File hash check here is for the downloaded Wabbajack file, this is usually not a line needed for support.

The Loading Modlists from Github is Wabbajack's Github Verification. an error line here would indicate either an outage with Github or an issue on the user's network.


![image](https://user-images.githubusercontent.com/38520983/154890578-fd57a16b-1145-4ea6-b11b-4c08160e4921.png)

Entries in the log that look something like this mean Wabbajack is having issues displaying thumbnail images for modlists in the gallery. This can generally be ignored but if these lines are present and the user is experiencing other network related problems like not being able to download the modlist file or issues with mod downloads it may point to a deeper issue.


![image](https://user-images.githubusercontent.com/38520983/154890328-d5b631ea-9c79-4e63-9d3d-e321ad6c5220.png)

Next are some lines indicating an install has been started. If these lines aren't present the user hasn't progressed far enough through the process to actually download a functioning Wabbajack file, so troubleshooting steps for issues that would be past this point generally wouldn't be needed. 

Any errors here would likely mean something is interfering with Wabbajacks Installer/VFS systems which may indicate Antivirus issues or folder permission issues (running in protected folders etc.)



![image](https://user-images.githubusercontent.com/38520983/154891524-3fa7de6e-7964-4172-8f51-b97c63a64a1f.png)

This section lists the various folders being used for each part of the install. In order:
* The install folder, where the list is being installed
* The downloads folder, where the mod files are being downloaded to
* the Game Folder, where Wabbajack thinks the Base Game is installed to
* and the Wabbajack folder, where Wabbajack is running from

The lines after this are Wabbajack's Drive Watcher entries, these should be checked to make sure there is sufficient room for an install. Wabbajack's "warning" levels are pitifully small and generally do not function well.

Some things to note about the Drive watcher:
* The drive that has the install folder should have enough room for the list install size + about 10gb or so. Generally if Wabbajack hits a drive space error it will be properly marked later in the log, but it's good to check here just in case.
* The drive with the download folder should have enough space for the total download size of the list.
* The drive with wabbajack should have around 20-50gb for temporary files during the hashing/extracting stage.

Generally users will run wabbajack from their C drive, which can sometimes be low on space especially as it's not usually associated with where Wabbajack ~needs~ space to be free, solutions would be running Wabbajack from another drive, but if their C drive is still very low on space they may need to clear some space even with Wabbajack running on a different drive.



![image](https://user-images.githubusercontent.com/38520983/154893313-aa8ae745-07f7-4ee3-b3b8-48d9d051bfe2.png)

These lines will only show if the user is updating a previous install or, for some insane reason the user is installing over the top of a different mod list.

Usually not a cause for support, but making sure the install folder and the list being installed matches in some form would be a good idea.

Following this will be a list of files being deleted, this can usually be ignored but any errors here usually indicate folder permission issues or possibly antivirus interference.



![image](https://user-images.githubusercontent.com/38520983/154894404-fe0035a3-f9f5-40a6-b612-59202eae39c9.png)


Otherwise you will see some general status lines from Wabbajack about what it's doing, and usually this will lead to starting the mod download process.

Nexus API errors will be covered in detail in the general issues section, but if the log abruptly ends here the general advice is to have the user try the install again, Wabbajack has a tendency to hang at this point if there are issues logging in to the API at any point.



![image](https://user-images.githubusercontent.com/38520983/154894690-2dadb491-589c-48ea-8a01-ae66f9c66aad.png)

Following this will be a list of all the mods that are being downloaded, any issues here can generally be ignored as they should be listed later at the end of the log if there are severe errors but if not there may be clues here. If there is *a lot* of errors in this section it can possibly mean there are other issues, usually network related.


For info on specific Download issues see the Wabbajack General Issues section.



![image](https://user-images.githubusercontent.com/38520983/154895098-9949c9e7-1bd7-4edb-afe5-c687b8ea3a49.png)

Past the download phase the install will move to extracting. 

First you'll see the file that's being extracted as well as it's location, this will typically be the `downloaded_mod_lists` folder. 

Most lines here can be ignored if they look similar to this image.

Errors here would usually mean something corrupt in the Wabbajack file, meaning it should be deleted from the `downloaded_mod_lists` folder located where Wabbajack is being run from and redownloaded from the Browse Modlist section in Wabbajack.



![image](https://user-images.githubusercontent.com/38520983/154895714-f28cc77d-0d46-4f03-b49f-9ef3832ceed6.png)

Next will be a list of all the mod files being extracted for the install. Errors here should be found and generally the line above the error will indicate which file the extraction is failing on.

Specific errors will be noted in the General Wabbajack Issues or the List specific section.


![image](https://user-images.githubusercontent.com/38520983/154895972-1a6563b5-e44d-4527-a1e2-0e2bfaa4b113.png)

And finally the end of a completed log.

These lines indicate Wabbajack doing finishing work like installing any inlined files included in the Wabbajack file, building BSA files, Generating merges and writing configuration files. etc.

Most of these lines should be self explanatory, and generally if an install progresses this far it's unlikely there will be issues here.

The `Skipping screen size remap` error line can usually be safely ignored. I can't get an answser to why it happens anywhere, but it doesn't seem to cause issues.

On ocassion an HTTP error can show here, which the install will *Fail* on, generally this means Wabbajack failed to show the readme page included with the Wabbajack file. While wabbajack technically calls this a failed install it *usually* means the install actually completed correctly.


And there you have it. a (reasonably) comprehensive breakdown of the typicall Wabbajack log file for a sucessful install. Further details on each section and specific erorr messsages and fixes will be in the general and temporary Wabbajack Issues section of this document.

Thank you for reading this far!






# General Issues



## General Wabbajack Issues

This section will detail common issues with Wabbajack installs. Where possible I will include screenshots of the errors, while this list is being curated I will substitute paraphrased error messages to the best of my recollection if I do not have a screenshot of the error. Please DM me any errors that I've missed or if you have screenshots of any yourself, or feel free to use a pull request, this is intented to be a community project.


  ### Wabbajack will not open correctly.
  
  ![image](https://user-images.githubusercontent.com/38520983/154899155-f61e3312-6027-4549-bbe1-f7abd42d928a.png)
  
  #### Wabbajack is stuck on a loading splash
  
  ###### Cause
    Unkown
  ###### Solution
    wjreset command

  ### Install Failed Errors
  
  ![image](https://user-images.githubusercontent.com/38520983/154900542-8c122467-9f36-4b66-88df-99a58b9827da.png)
  
  #### Install Failed with screenshot showing the Wabbajack UI log with 'Unable to download...' error visible.
  
  ###### Cause
    A mod file has failed to download
  ###### Solution
    Note which mod has failed and direct user to pinned solution for common failling files either in discord or the Readme. 
    If none exists check the Wabbajack log file.

  ![image](https://user-images.githubusercontent.com/38520983/154901280-95204c98-616e-496d-b399-45c692a78179.png)
  
  Wabbajack Log version of above error
  
  ###### Detailed Solution
  For errors in the log, note the download source in brackets after the file that is unable to be downloaded, in this example for a MEGA hosted download the link is displayed in full, copy pasting this link will lead to a download page for this mod if no mirror link exists in the readme or in the Discord pinned messages.
  
  For google drive links the log entry will end in `(GoogleDriveDownloader+State|1mfTQy2HIsdz8WWuTLDgiOR-t_IBZyTQC)` To generate a link to the file erroring take the string of letters and numbers after the `GoogleDriveDownloader+State|` part (remember to remove the bracket at the end of the line) and add it to the end of `https://drive.google.com/file/d/` so for example: `https://drive.google.com/file/d/1mfTQy2HIsdz8WWuTLDgiOR-t_IBZyTQC` 
  
  For Nexus file errors the log line will end in `(NexusDownloader+State|SkyrimSpecialEdition|19924|66001)` here the first part after the `NexusDownloader+State` will be the game category, the next is the Mod ID, and the last is the File ID. Finding the mod name is usually easy, but you can attach the Mod ID to the end of `https://www.nexusmods.com/skyrimspecialedition/mods/` to find the mod page. To find the File ID, go to the Files tab of the mod page and hover over the download button. in the bottom left corner of most browsers you will see a notification message that will say something like `https://www.nexusmods.com/Core/Libs/Common/Widgets/DownloadPopUp?id=66001&nmm=1&game_id=1704` the important information here is the number after `DownloadPopUp?id=` The number after this must match the File ID from the Wabbajack log. this is how you find the correct download the list requires without knowing it beforehand. If there are a lot of these Nexus errors in the log this can indicate network errors or in the case of users with Nexus Premium, the need to change the download location preferences in the Site Preferences > Premium Membership Preferences settings to something other than CDN or a different region location.
  
  The last source type that doesn't have a direct link are Base Game files. These are noted with log lines ending in `(GameFileSourceDownloader+State|SkyrimSpecialEdition|1.5.97.0|skyrimse.exe)` This shows the game required, and the version number listed here is the *expected* version, not what the user currently has. the last part is the file required. Generally a fix for these files is to verify the game install through Steam.
  
  
  
    



### General Living Skyrim Issues




### General Path of the Dovahkiin Issues




### General MOISE Issues




# Temporary Issues



### Temporary Wabbajack Issues




### Temporary Living Skyrim Issues




### Temporary Path of the Dovahkiin Issues







