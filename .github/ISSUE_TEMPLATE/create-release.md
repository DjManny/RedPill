# Create first GitHub release with prebuilt .saver binary

## Problem

There are currently zero releases. Users must build from source.

## Plan

1. Verify the build passes CI on `master`
2. Tag a release version (e.g., `v1.6.0`)
3. Build a Release `.saver` bundle
4. Create a GitHub release with the `.saver` attached

## Optional: Automated release workflow

```yaml
on:
  push:
    tags: ['v*']
jobs:
  release:
    runs-on: macos-latest
    steps:
      - uses: actions/checkout@v4
      - name: Build
        run: |
          xcodebuild -project RedPill.xcodeproj -scheme RedPill \
            -configuration Release build \
            CODE_SIGNING_ALLOWED=NO
      - name: Upload artifact
        uses: actions/upload-artifact@v4
        with:
          name: Red-Pill-saver
          path: build/Release/Red Pill.saver
```
