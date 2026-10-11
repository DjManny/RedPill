# Contributing to Red Pill

## Build & Test

1. Clone the repo and open `RedPill.xcodeproj` in Xcode.
2. Build with `Cmd+B` or from the command line:
   ```bash
   xcodebuild -project RedPill.xcodeproj -scheme RedPill -configuration Release build
   ```
3. The CI workflow runs on every push and PR — make sure it passes.

## Code Style

- A `.clang-format` file is included. Run `clang-format -i *.m *.h` before committing.
- Use 3-space indentation (matching the existing codebase).
- Keep the GPL v3 header at the top of every source file.

## Filing Issues

- Check existing issues before creating a new one.
- Include the macOS version and (if applicable) Xcode version.
- For build failures, paste the full `xcodebuild` output.

## Pull Requests

- Branch from `master`.
- Keep PRs focused — one feature or fix per PR.
- Squash commits before merging if there are many WIP commits.

## Metal Migration

If you're interested in helping migrate from OpenGL to Metal, please comment on the
Metal migration issue. The migration plan:

1. Replace `MatrixOpenGLView` with an `MTKView`-based view.
2. Port the fixed-function pipeline to Metal shaders.
3. Replace `GL_INTENSITY` texture with a Metal texture + shader modulation.
4. Test on macOS 13+ to verify compatibility.
