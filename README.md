# Build
cd /Users/zuofu/Documents/MacsyZones
xcodebuild -project MacsyZones.xcodeproj -scheme MacsyZones -configuration Release -derivedDataPath build

# Replace the app
cp -R build/Build/Products/Release/MacsyZones.app /Applications/

# Sign it
codesign --force --deep --sign - /Applications/MacsyZones.app

# Reset and re-grant Accessibility permission
tccutil reset Accessibility MeowingCat.MacsyZones

# Launch
open /Applications/MacsyZones.app
