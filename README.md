# Build and install MacsyZones

Run this one command. It quits the app, removes the old copy, builds,
installs, signs, and launches.

```bash
cd /Users/zuofu/Documents/MacsyZones && osascript -e 'quit app "MacsyZones"' 2>/dev/null; sleep 2; rm -rf /Applications/MacsyZones.app && xcodebuild -project MacsyZones.xcodeproj -scheme MacsyZones -configuration Release -derivedDataPath build && cp -R build/Build/Products/Release/MacsyZones.app /Applications/ && codesign --force --deep --sign - /Applications/MacsyZones.app && open /Applications/MacsyZones.app
```

## Notes

- `rm -rf` is needed. Without it, `cp -R` merges into the old bundle and
  leaves the old binary in place.
- The app must be quit first, or the files are in use.
- The app is removed before the build. If the build fails, there is no
  app in /Applications until you fix it and run again.
- Accessibility permission may need re-granting after the signature
  changes: System Settings > Privacy & Security > Accessibility.
- To force a permission reset, run this and re-grant:

```bash
tccutil reset Accessibility MeowingCat.MacsyZones
```

## Upstream

This fork tracks https://github.com/rohanrhu/MacsyZones

```bash
git fetch upstream && git rebase upstream/main
```
