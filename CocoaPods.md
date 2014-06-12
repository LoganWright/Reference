###Making an Existing Repository Available on CocoaPods 

- <a href="http://guides.cocoapods.org/making/making-a-cocoapod.html">CocoaPods Making a Pod</a>
- <a href="http://guides.cocoapods.org/making/getting-setup-with-trunk">Getting Set Up w/ Trunk</a>
- <a href="http://guides.cocoapods.org/syntax/podspec.html">Podspec Syntax Reference</a>

####Step 1. Create `.podspec` file

<b> Basic Template </b>
```
Pod::Spec.new do |s|
  s.name             = "SimpleCam"
  s.version          = "0.1.0"
  s.summary          = "<#summary#>"
  s.description      = "<#description#>"
  s.homepage         = "http://<#homepage#>.com"
  s.screenshots      = "<#screenshotURL#>", "<#anotherScreenshotURL#>"
  s.license          = {:type => '<#licenseType#>'}
  s.author           = { "<#yourName#>" => "<#yourEmail#>" }
  s.source           = { :git => "https://github.com/<#yourName#>/<#yourRepositoryName#>.git", :tag => s.version.to_s }
  s.social_media_url = 'https://twitter.com/<#yourTwitterHandle#>'

  s.platform     = :ios, '5.0'
  # s.ios.deployment_target = '5.0'
  # s.osx.deployment_target = '10.7'
  s.requires_arc = true

  s.source_files = '<#pathToFiles#>/<#className#>.{h,m}'
  s.resources = '<#pathToFiles#>/*.png'
  # includes all .png resources in file

  # SET DEPENDENCIES
  
  # s.ios.exclude_files = '<#pathToOSXFiles#>'
  # s.osx.exclude_files = '<#pathToIOSFiles#>'
  # s.public_header_files = 'Classes/**/*.h'
  # s.frameworks = 'SomeFramework', 'AnotherFramework'
  # s.dependency 'JSONKit', '~> 1.4'
end
```

*Add .podspec to project folder*

####Step 2: Create `LICENSE` (if necessary)

CocoaPods requires a license file, make sure one is included

*Add LICENSE to project folder*

####Step 3: Prep Git For Release

```
$ git add -A && git commit -m "Release 0.0.1"
$ git tag '0.0.1'
$ git push --tags
```

####Step 4: Configure Trunk (if necessary)

```
$ pod trunk register yourName@cocoapods.org 'Your Name' --description='macbook air'
```

This will send an email to authorize your computer.  Accept it.

####Step 5: Test PodSpec

```
$ cd path/to/project
$ pod lib lint
```

####Step 6: Push To Trunk

```
$ pod trunk push <#yourPodspec#>.podspec
```

####Step 7: Profit

Or don't, cuz this is open-source!


###Using CocoaPods in a Project

####Step 1: Create Project 

Create your project if you haven't already

####Step 2: Create Podfile

In Terminal

#####1:
```
cd path/to/project
```

#####2:

```
subl Podfile
```

Assuming you have sublime command line tools installed in your terminal, this will create a new file named 'Podfile'.  You can look at how to install sublime command line tools <a href="http://www.sublimetext.com/docs/2/osx_command_line.html">here</a>.

####Step 3: Add dependencies to your podfile

Basic Template Example

```
platform :ios, '6.0'

pod 'SVProgressHUD'
pod 'AFNetworking'
pod 'SimpleCam'
```

etc ...

####Step 4: Add .gitignore

Add this to make sure your that everything in your `Pods/` folder is not included in your repository

```
Pods/
```

####Step 5: In Command Line

```
pod install
```

####Step 6: Close your project if it is open and from now on use `<#YourProjectName#>.xcworkspace`

If you don't, there will be errors.









