# osx-plist-finder
An OS X Automator workflow that locates the preferences plist for OS X Applications

## Usage
Highlight an OS X application in Finder - typically in the /Applications or /Applications/Utilites folder - right-click, and select __findPlist__ from the Services menu. If the preferences plist can be found in the User Preferences location (~/Library/Preferences), it will be revealed in a Finder window.

## Installation
Automator workflows are stored as application packages - albeit with a `.workflow` extension - in ~/Library/Services.

#### obtain the `.workflow` package
 - via git clone...

    `git clone https://github.com/cognivator/osx-plist-finder.git`<br/>
    -OR-<br/>
    Use the Open in Github Desktop button (next to Download ZIP button)
 - via raw download...
   1. Use the __Download ZIP__ button
   2. Extract the zip file to expand the project files

#### install the workflow
 1. extract FindPlist.workflow.zip
 2. make findPlist.workflow available as a workflow service
   - via Automator...
     1. Double-click, or right-click > Open the findPlist.workflow file
     2. Choose to Install the workflow
  - via file copy...
     1. copy findPlist.workflow to ~/Library/Services


## Operation
The workflow follows this sequence,
 1. check if the selected item in Finder is an application package (extension is .app)
 2. locate Contents/Info.plist in the application package
 3. extract the `CFBundleIdentifier` property from Info.plist. This should be the name of the application preferences plist file, minus the `.plist` extension.
 4. reveal the preferences plist file in User Preferences (~/Library/Preferences) in a Finder window, if the plist file exists

The workflow is defined as an Automator Service, activated for Files or Folders in any application. This allows the workflow to appear in the Services context menu, exspecially in Finder. The service may be available in other applications, but none have been tested except for Finder.

The workflow comprises native Automator Finder actions, Applescript and Javascript actions, and system variables. Generally, folder navigation is handled by the Finder actions and system variables, verification of folder contents is handled by Applescript actions, and plist operations are handled by Javascript action.

## Known Limitations
 * test with OS X Yosemite 10.10.5
 * only the user preferences location is checked for the plist file (~/Library/Preferences)
 * if a preferences plist file cannot be found, there is no messaging and no Finder window; the failure is silent.

## License
MIT
