require 'tmpdir'

desc 'Run unit tests on the specified version of Swift'
task :test  do
  sh "set -o pipefail && xcodebuild -workspace 'Bootstrap/Bootstrap.xcworkspace' -sdk 'iphonesimulator' -scheme 'Bootstrap' -destination 'name=iPhone 8' SWIFT_VERSION=#{ENV['SWIFT_VERSION']} build test | tee output/xcodebuild_swift#{ENV['SWIFT_VERSION']}.log | xcpretty --color --simple"
end

desc 'Lint the library for CocoaPods usage'
task :pod_lint do
  sh 'bundle exec pod lib lint --allow-warnings'
end

desc 'Run a local copy of Carthage on a temporary directory'
task :carthage do
  sh 'set -o pipefail && carthage bootstrap --platform iOS && xcodebuild | xcpretty --color --simple'
end

desc 'Runs SwiftLint'
task :swiftlint do
  sh 'swiftlint lint --no-cache'
end
