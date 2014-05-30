###Adding CocoaPods To Existing Repository

- <a href="http://guides.cocoapods.org/making/making-a-cocoapod.html">CocoaPods Making a Pod</a>
- <a href="http://guides.cocoapods.org/making/getting-setup-with-trunk">Getting Set Up w/ Trunk</a>

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



