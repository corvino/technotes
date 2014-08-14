#OS X Setup
***

#### Adium
- Copy **~/Library/Application Support/Adium 2.0**

#### Skype
- Copy **~/Library/Application Support/Skype**
- Optionally, additionally copy **~/Library/Preferences/com.skype.skype.plist**

#### XCode Preferences
- Keybindings in Xcode 5 are stored as **.pbxkeys** files in **~/Library/Developer/Xcode/UserData/KeyBindings/**
    - Prior to Xcode 5, these files were stored in **~/Library/Application Support/Xcode/Key Bindings**

#### IntelliJ IDEA Preferences
- Preferences are stored in **~/Library/Preferences/IntelliJIDEA##** or **~/Library/Preferences/IdeaIC##**, where **##** is a version number.
    - Keymaps are stored in **/keymaps** relative to the preference directory.
    - Colors are stored in **/colors** relative to the preference directory.

### Preferences
- **System Prefernces ->**
    - **General ->** Recent items: 50?
    - **Keyboard -> Keyboard ->** Use all F1, F2, etc. keys as standard function keys: NO
    - **Sound -> Sound Effects ->** Play feedback when volume is changed: NO
- **Terminal -> Settings -> Keyboard ->** Use option as meta key: YES
- **Finder -> General ->** Open folders in tabs instead of new windows: NO

### Miscellaneous
- Quicklook plugin for .mobileprovision files.
    - https://github.com/chockenberry/Provisioning
- sudo ln -s /System/Library/Frameworks/JavaScriptCore.framework/Versions/Current/Resources/jsc /bin/jsc
