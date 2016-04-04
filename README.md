# osx-plist-finder
An OS X Automator workflow that locates the preferences plist for OS X Applications

## Usage
Highlight an OS X application in Finder - typically in the /Applications folder - right-click, and select __findPlist__ from the Services menu. If the preferences plist can be found in the User Preferences location (~/Library/Preferences), it will be revealed in a Finder window.

## Installation
WIP

## Operation
The workflow follows this sequence,
 1. check if the selected item in Finder is an application package (extension is .app)
 2. locate Contents/Info.plist in the application package
 3. extract the `CFBundleIdentifier` property from Info.plist. This should be the name of the preferences plist file.
 4. reveal the preferences plist file in User Preferences (~/Library/Preferences) in a Finder window, if the plist file exists

The workflow comprises native Automator Finder actions, Applescript and Javascript actions, and system variables. Generally, folder navigation is handled by the Finder actions and system variables, verification of folder contents is handled by Applescript actions, and plist operations are handled by Javascript action. 

## Known Limitations
 * Currently the only preferences location explored is User Preferences (~/Library/Preferences).
 * If a preferences plist file cannot be found, there is no messaging and no Finder window. The failure is silent.

## License
MIT
