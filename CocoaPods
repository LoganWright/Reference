###Adding CocoaPods To Existing Repository

####Step 1. Create `.podspec` file

<b> Basic Template </b>
```
#
# Be sure to run `pod lib lint NAME.podspec' to ensure this is a
# valid spec and remove all comments before submitting the spec.
#
# To learn more about a Podspec see http://guides.cocoapods.org/syntax/podspec.html
#
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
  s.social_media_url = 'https://twitter.com/logmaestro'

  s.platform     = :ios, '5.0'
  # s.ios.deployment_target = '5.0'
  # s.osx.deployment_target = '10.7'
  s.requires_arc = true

  s.source_files = '<#pathToFiles#>/<#className#>.{h,m}'
  s.resources = '<#pathToFiles#>/*.png'
  # includes all .png resources in file

  # s.ios.exclude_files = 'Classes/osx'
  # s.osx.exclude_files = 'Classes/ios'
  # s.public_header_files = 'Classes/**/*.h'
  # s.frameworks = 'SomeFramework', 'AnotherFramework'
  # s.dependency 'JSONKit', '~> 1.4'
end
```
