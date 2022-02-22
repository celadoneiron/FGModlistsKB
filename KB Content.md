# **Contents**

### **Reading Wabbajack Logs**
  [Wabbajack Logs 101](#wabbajack-logs-101)

### **General Issues**
  
  * [Wabbajack - General Issues](#general-wabbajack-issues)
  
  * [Wabbajack will not open correctly](#wabbajack-will-not-open-correctly)
    * [Wabbajack is stuck on a loading splash](#wabbajack-is-stuck-on-a-loading-splash)
  
  * [Wabbajack will not start the modlist installation](#wabbajack-will-not-start-the-modlist-installation)
    * [Wabbajack is stuck on the select install and download location screen](#wabbajack-is-stuck-on-the-select-install-and-download-location-screen)
  
  * [Install Failed Errors]()
    * [Install Failed with screenshot showing the Wabbajack UI log with 'Unable to download...' error visible.](#install-failed-with-screenshot-showing-the-wabbajack-ui-log-with-unable-to-download-error-visible)
    * [Install Failed - Out of Memory error](#install-failed---out-of-memory-error)
    * [Installation Failed - 7zip Return Error](#installation-failed---7zip-return-error)
    * [Installation Failed - 7zip Return Error -- Not Enough Space](#installation-failed---7zip-return-error----not-enough-space)
  
  
  
  
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

---

![image](https://user-images.githubusercontent.com/38520983/154885616-de500839-1a38-4c07-8326-264054c214e9.png)

Here is the beginning of a log file. The first line shows you the Wabbajack build version, this is usually not needed for support issues.

The second line shows the current location wabbajack is running in. This can be useful in several different ways, chiefly, making sure Wabbajack isn't being run from any protected windows locations such as: The Desktop, Documents, Pictures, Downloads, etc. While sometimes this may not be an issue at all it is a good thing to check first and possibly make the user aware that you can run into errors with Wabbajack in any of these locations - Good advice to fix: have them run wabbajack from it's own folder `C:\Wabbajack` or similar.

The Third line shows the current Operating System version. Usually not an issue for support, but the general consensus is that running Wabbajack and by extention most modlists on anything prior to Windows 10 will lead to issues.

The next two lines show general system information such as the amount of RAM available as well as the display settings and video memory size, as well as a warning if the pagefile for the system is below 20000MB. While generally not useful for diagnosing Wabbajack issues it can be helpful to check and advise the user if their system specs seem especially low for the requirements of the list. Pagefile can be an issue if Wabbajack is reporting out of memory errors.

You may also see an entry around this point of the log saying: `Outside of standard install folder, not updating` This generally means the user is running wabbajack from inside the Version folder for wabbajack and not using the main launcher. While typically not a problem it can cause issues if the list requires a newer version of Wabbajack than the version they are currently running. Otherwise this line can generally be ignored.

---

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

---

![image](https://user-images.githubusercontent.com/38520983/154888204-02e1d077-5700-4674-9007-41d3567e8629.png)

The next section in a log will be the other Game Finder locations, such as Origin, Epic Game Store, GOG etc. This is currently only relevant for MOISE support, further information will be in MOISE general issues.

---

![image](https://user-images.githubusercontent.com/38520983/154889570-d4ac5e65-8b81-489e-8aa5-6aec636ec554.png)

Next we have lines showing the Wabbajack version. This should generally always be the latest version of Wabbajack, if an older version of Wabbajack is being used to install a list that was compiled on a newer version the list will not install and an error will be displayed on the screen where the user selects the install and download paths. 

Next are some entries showing the status of the Wabbajack build server. If this shows anything other than `Build Server is alive` this will usually indicate either an error on the users side or an error with the connection to the Wabbajack build server, unfortunately it's usually difficult to tell which. It would be best to check the wabbajack discord if this is an issue multiple users are having it can generally be assumed it's an issue on Wabbajacks side.

The File hash check here is for the downloaded Wabbajack file, this is usually not a line needed for support.

The Loading Modlists from Github is Wabbajack's Github Verification. an error line here would indicate either an outage with Github or an issue on the user's network.

---

![image](https://user-images.githubusercontent.com/38520983/154890578-fd57a16b-1145-4ea6-b11b-4c08160e4921.png)

Entries in the log that look something like this mean Wabbajack is having issues displaying thumbnail images for modlists in the gallery. This can generally be ignored but if these lines are present and the user is experiencing other network related problems like not being able to download the modlist file or issues with mod downloads it may point to a deeper issue.

---

![image](https://user-images.githubusercontent.com/38520983/154890328-d5b631ea-9c79-4e63-9d3d-e321ad6c5220.png)

Next are some lines indicating an install has been started. If these lines aren't present the user hasn't progressed far enough through the process to actually download a functioning Wabbajack file, so troubleshooting steps for issues that would be past this point generally wouldn't be needed. 

Any errors here would likely mean something is interfering with Wabbajacks Installer/VFS systems which may indicate Antivirus issues or folder permission issues (running in protected folders etc.)

---

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

---

![image](https://user-images.githubusercontent.com/38520983/154893313-aa8ae745-07f7-4ee3-b3b8-48d9d051bfe2.png)

These lines will only show if the user is updating a previous install or, for some insane reason the user is installing over the top of a different mod list.

Usually not a cause for support, but making sure the install folder and the list being installed matches in some form would be a good idea.

Following this will be a list of files being deleted, this can usually be ignored but any errors here usually indicate folder permission issues or possibly antivirus interference.

---

![image](https://user-images.githubusercontent.com/38520983/154894404-fe0035a3-f9f5-40a6-b612-59202eae39c9.png)


Otherwise you will see some general status lines from Wabbajack about what it's doing, and usually this will lead to starting the mod download process.

Nexus API errors will be covered in detail in the general issues section, but if the log abruptly ends here the general advice is to have the user try the install again, Wabbajack has a tendency to hang at this point if there are issues logging in to the API at any point.

---

![image](https://user-images.githubusercontent.com/38520983/154894690-2dadb491-589c-48ea-8a01-ae66f9c66aad.png)

Following this will be a list of all the mods that are being downloaded, any issues here can generally be ignored as they should be listed later at the end of the log if there are severe errors but if not there may be clues here. If there is *a lot* of errors in this section it can possibly mean there are other issues, usually network related.


For info on specific Download issues see the Wabbajack General Issues section.

---

![image](https://user-images.githubusercontent.com/38520983/154895098-9949c9e7-1bd7-4edb-afe5-c687b8ea3a49.png)

Past the download phase the install will move to extracting. 

First you'll see the file that's being extracted as well as it's location, this will typically be the `downloaded_mod_lists` folder. 

Most lines here can be ignored if they look similar to this image.

Errors here would usually mean something corrupt in the Wabbajack file, meaning it should be deleted from the `downloaded_mod_lists` folder located where Wabbajack is being run from and redownloaded from the Browse Modlist section in Wabbajack.

---

![image](https://user-images.githubusercontent.com/38520983/154895714-f28cc77d-0d46-4f03-b49f-9ef3832ceed6.png)

Next will be a list of all the mod files being extracted for the install. Errors here should be found and generally the line above the error will indicate which file the extraction is failing on.

Specific errors will be noted in the General Wabbajack Issues or the List specific section.

---

![image](https://user-images.githubusercontent.com/38520983/154895972-1a6563b5-e44d-4527-a1e2-0e2bfaa4b113.png)

And finally the end of a completed log.

These lines indicate Wabbajack doing finishing work like installing any inlined files included in the Wabbajack file, building BSA files, Generating merges and writing configuration files. etc.

Most of these lines should be self explanatory, and generally if an install progresses this far it's unlikely there will be issues here.

The `Skipping screen size remap` error line can usually be safely ignored. I can't get an answser to why it happens anywhere, but it doesn't seem to cause issues.

On ocassion an HTTP error can show here, which the install will *Fail* on, generally this means Wabbajack failed to show the readme page included with the Wabbajack file. While wabbajack technically calls this a failed install it *usually* means the install actually completed correctly.

---

And there you have it. a (reasonably) comprehensive breakdown of the typicall Wabbajack log file for a sucessful install. Further details on each section and specific erorr messsages and fixes will be in the general and temporary Wabbajack Issues section of this document.

Thank you for reading this far!




# General Issues



## General Wabbajack Issues

This section will detail common issues with Wabbajack installs. Where possible I will include screenshots of the errors, while this list is being curated I will substitute paraphrased error messages to the best of my recollection if I do not have a screenshot of the error. Please DM me any errors that I've missed or if you have screenshots of any yourself, or feel free to use a pull request, this is intented to be a community project.

---

  ## Wabbajack will not open correctly.
  
  
  
  ![image](https://user-images.githubusercontent.com/38520983/154899155-f61e3312-6027-4549-bbe1-f7abd42d928a.png)
  
  #### Wabbajack is stuck on a loading splash
  
  ###### Cause
    Unkown
  ###### Solution
    wjreset command

---

  ## Wabbajack will not start the modlist installation
  
  ![image](https://user-images.githubusercontent.com/38520983/154907701-94b2a129-2c20-4118-b306-1c86af9d73a7.png)
  
  #### Wabbajack is stuck on the select install and download location screen
  
  ###### Cause
    Incorrect Wabbajack version
    Incorrect install location
  ###### Solution
    Have the user hover over the exclamation mark to determine error. Follow fixes for the various causes in detailed solution. 
    If no error shown on hover assume old wabbajack version have the user update. otherwise wjreset command.
    
  ###### Detailed Solution
  
  Errors on this screen are typically self explanatory. Having the user hover over the exclamation mark will usually result in figuring out the issue. 

  For error messages that say `The Modlist you are trying to install was made using a newer Version of Wabbajack` Instruct the user to either update Wabbajack by running the main launcher, as this typically occurs when the user is running Wabbajack from inside the version folder. Or have them download Wabbajack fresh from the website and replace their existing install.
  
  For error messages that say `Either delete everything except the downloads folder, or pick a new location. Cannot install to this folder as it has unexpected files` This is typically caused by the user installing to a blacklisted location, such as Desktop, Documents, Downloads etc. or they are installing to a folder that has files in it other than the default 'downloads' folder. The simpilest solution for this error is to have them create a new folder in the root of their drive named after the modlist and install there. If the user is partially through a modlist install already be sure to double check where they have set as their download location to make sure they don't download mods a second time.
  
  ---
  
  ## Installation Failed Errors
  
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
  
  The last source type that doesn't have a direct link are Base Game files. These are noted with log lines ending in `(GameFileSourceDownloader+State|SkyrimSpecialEdition|1.5.97.0|skyrimse.exe)` This shows the game required, and the version number listed here is the *expected* version, not what the user currently has. the last part is the file required. Generally a fix for these files is to verify the game install through Steam. As a special note for this type of error if the only file failing is the `Skyrim_Default.ini` ensure the user has their game language set to English in Steam.
  
 ---
 
  ![image](https://user-images.githubusercontent.com/38520983/154915579-d4a6862a-d461-4fdb-b2db-0eb1c1ee02fe.png)
  
  #### Install Failed - Out of Memory error
  
  ###### Cause
    Lack of System Memory or too low pagefile size
    
  ###### Solution
    Pagefile command or check WJ log for amount of system ram
    
  ###### Detailed Solution
  
  This is a decidedly rare error when WJ is installing a mod list but it can happen. Generally setting a larger pagefile will fix this but on occassion a user may attempt to install the list with a very small amount of system RAM.
  
 --- 
 
 ![image](https://user-images.githubusercontent.com/38520983/154916494-d29adbef-0ea2-4086-9606-ea2d459bdf56.png)
 
  
  #### Installation Failed - 7zip Return Error
  
  ###### Cause
    File being extracted is corrupt
 
  ###### Solution
    Check Wabbajack log for specific file that is erroring. Have user delete and redownload the file.
  
  ###### Detailed Solution
  Generally this error indicates a corrupt file of some kind. Look back in the log from where this error occurred and try to find the most recent file it was extracting. It most commonly occurs when extracting the Wabbajack file at the end of an install but not always. Have the user close Wabbajack, delete the file in Windows Explorer and then try the install again. **Do not confuse this error with a similar 7zip Error that mentions the user has run out of hard drive space.**

---

  ![image](https://user-images.githubusercontent.com/38520983/154918041-5ae0524c-c757-44f3-aea2-b72dc08aec9a.png)

  #### Installation Failed - 7zip Return Error -- Not Enough Space
  
  ###### Cause
    Not enough space on the Installation drive.
  
  ###### Solution
    Have user free up disk space
  
  ###### Detailed Solution
  
  This error will generally occur at the end of an install when mods or the Wabbajack file are extracting. Checking the Drive Watcher section of the log is a good first step. You can generally determine which drive is low on space from there. If all the drives mentioned in the Drive Watcher have ample space, assume the C drive is the culprit even if it's not listed in the Drive Watcher, and have the user free some space there if possible.
  
---

![image](https://user-images.githubusercontent.com/38520983/155055630-40a8da90-d213-4160-810f-abc037909071.png)

#### Installation Failed - HttprequestException: No Such Host is known.

###### Cause
    The host website noted in the error message is down or unreachable
  
###### Solution
    Wait for the website to return to service

###### Detailed Solution

This error is caused when a website that Wabbajack needs to connect to is experiencing issues. Typically this will be Github or the Wabbajack build server, but it could occassionally happen to Nexus or other mod hosting websites. There is little that can be done to fix this other than wait for service to be restored.

---

![image](https://user-images.githubusercontent.com/38520983/155056472-38880fda-0d34-4a9b-b369-451334991908.png)

#### Install Failed - HttpRequestException: No Connection could be made because the target machine actively refused it

###### Cause
    Networking error, target machine is refusing connection to the user
    
###### Solution
    Network work around option in WJ settings, or VPN.
    
###### Detailed Solution

Network errors are difficult to solve, trying the Network workaround option or a VPN can be good first steps, if the issue perissts it's likely an error with the users network settings, if you have the knowledge and time to devote to helping them sort this out feel free, but it can simply be considered outside the scope of support for the modlist.

---

![image](https://user-images.githubusercontent.com/38520983/155058303-db3f30a4-9146-4487-a3b4-9e40da770da3.png)

#### Install Failed - 'Error'

###### Cause
    Insufficient Hard Drive space

###### Solution
    Have user free space on the Drive(s) their install and download folder are located on as well as possibly their Windows Drive

#### Detailed Solution

This is a rarer error type that seems to be a combination of the Drive Watcher for Wabbajack not reacting and Wabbajack running out of space during the download phase as opposed to the install phase. If there are seemingly no other causes to the install failing and only this single line 'Error' in the log be sure to check the Drive Watcher section of the log to check the free space at the start of the install attempt and do your best judgement if it could be the issue, sometimes it is difficult to tell how much space is required when a user is mid-install.

---

![image](https://user-images.githubusercontent.com/38520983/155059364-60b8ed81-98f3-4ee4-a97d-cb3aa8e93b83.png)

#### Install Failed - Invalid File Format

###### Cause
    File in error line is incorrect/corrupted
    
###### Solution
    Have user delete file noted in the error message and download again
    
###### Detailed Solution

This error is usually found during the extraction phase of the install, rarely from a mod file but usually from the Wabbajack file itself. The specific file that is erroring is noted in the error line in the Wabbajack log, as well as the location of said file. Direct the user to find the file at the path in the error message, delete it and obtain the file again. For Wabbajack files this is by browsing the modlist gallery in the app and clicking the download button again. For erroring mod archives, simply run the Wabbajack installer again.

---

![image](https://user-images.githubusercontent.com/38520983/155059780-ea1a7995-7e5d-4153-98c5-fff2640d1a2a.png)

#### Install Failed - Cannot run inside xxx

###### Cause
    User is attempting to run wabbajack from a blacklisted location
    
###### Solution
    Have user move their wabbajack files to it's own folder at the root of the drive

###### Detailed Solution

This is Wabbajack's sanity check to avoid the program running in Windows Protected locations, you can double check by looking at the beginning of the log to find where Wabbajack is running in. Note that this does not stop users *installing* modlists in Windows Protected locations so a good follow up is to make sure their install/download locations aren't also in one of these locations

---

![image](https://user-images.githubusercontent.com/38520983/155060274-e6cd1415-9c88-4074-9c2f-a5c0bc24844a.png)

#### Install Failed - Out of Memory Exception

###### Cause
    Wabbajack has run out of memory
    
###### Solution
    pagefile command or check physical memory amount
    
###### Detailed Solution

This error is relatively rare, Check the pagefile amount at the begining of the log and have the user increase it following the pagefile command, if this doesn't solve the issue check the phsyical amount of memory reported, if the error persists it could indicate issues with the users actual physical memory.

---

![image](https://user-images.githubusercontent.com/38520983/155060629-122c34bd-530b-4559-bc00-13389cca5b93.png)

#### Install Failed - Could not find the game folder

###### Cause
    Wabbajack could not find the game folder
    
###### Solution
    Ensure game is actually installed, Run game once from steam
    
###### Detailed Solution

This error occurs when Wabbajack cannot find the Game Files that the list requires, generally this will mean either:
  * The user has moved the game files from where Steam expected them to be
  * The user hasn't run the game once since installing so registry entries may not be present
  * The user doesn't actually have the game installed
  * The user is pirating the game (or rarely some other pirated game has overwritten the registry)

This is best checked through the Game Finder list in the Wabbajack log. If there is no entry there for the game required to install the list, check to make sure the user has it installed, if it *is* present there ensure with the user that the location listed is where they have the game files, users tend to copy/paste Steam game files to move them out of Program Files etc. If none of these solutions help the next steps would be to check for piracy, usually by getting a screenshot of the user's game folder, there are pins in the discord to help identify piracy. Reinstalling the game from scratch would be the only further troubleshooting for this issue unless it is a very specific list problem.

****** Additional note on piracy

![image](https://user-images.githubusercontent.com/38520983/155061384-28eb8b29-cbf6-4626-9d83-3d20b7bbef48.png)

Probably very rarely the above issue can be caused by other pirated software, as you can see in the screenshot the entirety of the steam registry entries are pointing to one Steam game that doesn't not have a typical Steam Library path that includes `steamapps/common` therefore they should remove this software and reinstall Steam entirely to refresh it's registry entries.

---

![image](https://user-images.githubusercontent.com/38520983/155062186-800353db-7234-4f88-b907-d2b3fdf4abca.png)

#### HttpRequestException Error while Copying content to a stream

###### Cause
    Unkown, some type of HTTP error

###### Solution
    Vpn or Wabbajack workaround
    
###### Detailed Solution
    
Most HttpRequestException errors will have little troubleshooting steps other than suggestions of using the Network Workaround setting or a VPN, a good followup question if these solutions don't work is asking if the user is connected to public or restricted WIFI networks (such as at a school or dorm setting, etc.) Obviously there is little we can do to help with network issues on the user end

---





### General Living Skyrim Issues

This section will detail specific issues to the Living Skyrim 3 Modlist that are unlikely to be resolved within 1 or 2 patches to the modlist but are issues that repeatedly arise in doing support for the list. Generally fixes to these issues will be pinned in the various support channels but they will be detailed here to help both identify the issues and allow you to know which pinned message to direct the user to.

---




### General Path of the Dovahkiin Issues




### General MOISE Issues




# Temporary Issues



### Temporary Wabbajack Issues




### Temporary Living Skyrim Issues




### Temporary Path of the Dovahkiin Issues







