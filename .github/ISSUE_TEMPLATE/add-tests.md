# Add unit tests for animation logic

## Problem

The repository currently has zero tests. The animation logic in `MatrixStrip.m` contains complex state machines that would benefit from automated verification.

## What to Test

### MatrixStrip
- `initWithCells:x:y:z:params:` — Verify all arrays are allocated and initialized
- `randomizeCursorState:` — Test state machine transitions (live → static → empty → live)
- `computeColorVertices` — Verify color cycling math
- `computeTextureVertices:` — Verify glyph texture coordinate calculations
- `computeQuadVertices:x:y:z:` — Verify visible cell range detection
- `animateSelfIsComplete` — Test cursor movement, cell aging, strip lifecycle completion

### MatrixTexture
- `loadFromFile:` — Verify texture loading and memory allocation
- `loadBitmap:` — Verify bitmap data flipping and format detection

## Approach

- Use XCTest framework
- Add a separate test target in the Xcode project
- Focus on pure logic rather than GL calls
- For GL-dependent methods, extract math into testable helper methods

## CI Integration

Add a test step to the GitHub Actions workflow:
```yaml
- name: Run Tests
  run: |
    xcodebuild test \
      -project "$PROJECT" \
      -scheme "$SCHEME" \
      -configuration Debug \
      CODE_SIGNING_ALLOWED=NO
```
