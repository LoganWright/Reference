#Cocoapods

##Installing Cocoapods

- Open Terminal
- Enter command: `sudo gem install cocoapods`
- Enter your password

> Wait for this to finish, don't touch your terminal.  It might take a couple minutes

##Setting Up Command Line Text Editor

#####Sublime

- Download Sublime <a href="http://www.sublimetext.com/">here</a>
- Install commandline tools following instructions <a href="http://www.sublimetext.com/docs/2/osx_command_line.html">here</a>

#####Atom (My Preference)

- Download Atom <a href="https://atom.io/">here</a>
- Install atom commandline tools by opening Atom and selecting `Atom > Install Shell Commands`

>Continuing forward, all commandline references will use the `atom` keyword.  Replace this with whatever you have designated as your text editor.

##Setting Up Cocoapods

###New Project

- Create your Xcode Project
- Make sure that `Create git repository` is selected
> If you forgot to select this, just continue to the `Existing Project` section

###Existing Project

- Open terminal
- Enter command `cd ~/path/to/your/project`
- Enter command `git init`

###Setup Gitignore

- Open terminal
- Enter command `cd ~/path/to/your/project` (if necessary)
- Enter command `atom .gitignore`
- Add `Pods/` to your gitignore
- If your `.gitignore` is empty, add the following:

```
# Xcode
#
build/
*.pbxuser
!default.pbxuser
*.mode1v3
!default.mode1v3
*.mode2v3
!default.mode2v3
*.perspectivev3
!default.perspectivev3
xcuserdata
*.xccheckout
*.moved-aside
DerivedData
*.hmap
*.ipa
*.xcuserstate

# CocoaPods
#
# We recommend against adding the Pods directory to your .gitignore. However
# you should judge for yourself, the pros and cons are mentioned at:
# http://guides.cocoapods.org/using/using-cocoapods.html#should-i-ignore-the-pods-directory-in-source-control
#
Pods/
```

- Save your `.gitignore` file <key>cmd</key> + <key>s</key>

##Add Podfile

- Open terminal
- Enter command `cd ~/path/to/your/project`
- Enter command `atom Podfile`
> This is case SENSITIVE

###Source

Add a source to the top of your `Podfile`.  If you're unsure what this should be, it should be this:

`source 'https://github.com/CocoaPods/Specs.git'`

###Platform

Specifying a platform is unncessary, but highly encouraged.  The syntax is:

`platform :<#platform#>, '<#minimum version#>'`

Example:

`platform :ios, '7.0'`

###Add Pods

You add pods to your project using the following syntax:

`pod '<#pod name#>', '<#pod version'`

A simple example would look like this:

`pod 'AFNetworking', '1.0'`

Or, to get the latest version, you can omit the version from the declaration:

`pod 'AFNetworking'`

There are more complex arguments regarding version available <a href="http://guides.cocoapods.org/syntax/podfile.html#pod">here</a>

###Basic `Podfile` Example

```
source 'https://github.com/CocoaPods/Specs.git'

platform :ios, '7.1'

pod 'SVProgressHUD'
pod 'AFNetworking'
```

> If you already have a workspace created, you'll need to specify this in your podfile by adding: `workspace 'MyWorkspace'`

##Importing Dependencies

Now we're going to integrate our libraries into the Xcode project.  

- Close Xcode Project
- Open Terminal
- Enter command `cd ~/path/to/your/project`
- Enter command `pod install`
> Wait for this to finish, depending on the requirements of the `Podfile`, particularly with new projects, this may take a minute or two.  Just leave it.

##Advanced Podfile (in progress)

More on the Podfile: http://guides.cocoapods.org/using/the-podfile.html

###Pod Errors

Occasionally, imported libraries will have errors  or warnings generated in Xcode, these can be silenced if desired by adding the following to the `Podfile`

`inhibit_all_warnings!`

To prevent warnings on a library specific basis, you can use the following syntax:

`pod 'SomePodWithWarnings', :inhibit_warnings => true`
