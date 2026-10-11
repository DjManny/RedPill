# Clarify and consolidate Info.plist vs Info-RedPill.plist

## Problem

Two Info.plist files exist with overlapping but inconsistent content:

| Field | `Info.plist` | `Info-RedPill.plist` |
|-------|-------------|---------------------|
| `CFBundleExecutable` | `${EXECUTABLE_NAME}` | `Red Pill` |
| `CFBundleIdentifier` | `$(PRODUCT_BUNDLE_IDENTIFIER)` | `com.ath0.redpill` |
| `CFBundleShortVersionString` | `$(MARKETING_VERSION)` | `1.5.0` |
| `CFBundleVersion` | `$(CURRENT_PROJECT_VERSION)` | `1.5.0` |

## Actions

1. Determine which plist is used — check `RedPill.xcodeproj/project.pbxproj` for `INFOPLIST_FILE`
2. Delete the unused one
3. Consider updating the bundle identifier from `com.ath0.redpill` to `com.djmanny.redpill`
