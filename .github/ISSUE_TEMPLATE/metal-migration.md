# Migrate from deprecated OpenGL to Metal

## Problem

Apple deprecated OpenGL in macOS 10.14 (Mojave). This screensaver relies heavily on legacy OpenGL:

- `GL_INTENSITY` textures
- Fixed-function pipeline (`glBegin`/`glEnd`-style rendering)
- `glVertexPointer`/`glColorPointer`/`glTexCoordPointer` client state arrays
- `glTexImage2D` for texture loading
- `gluPerspective` for projection
- `GL_FOG` for depth effects

On macOS 13+ (Ventura and later), OpenGL support is increasingly unreliable.

## Migration Plan

1. Replace `MatrixOpenGLView` with an `MTKView`-based view
2. Port the fixed-function pipeline to Metal shaders:
   - Vertex shader for quad rendering (position + color + texture coords)
   - Fragment shader for texture modulation (replacing `GL_INTENSITY` + `GL_MODULATE`)
   - Fog calculation in the fragment shader (replacing `GL_FOG`)
3. Replace `GL_INTENSITY` texture with a Metal texture + shader modulation
4. Replace `gluPerspective` with a manual perspective matrix calculation
5. Replace `glVertexPointer`/`glColorPointer`/`glTexCoordPointer` with Metal vertex buffers
6. Replace `GL_QUADS` drawing with Metal render command encoders using triangle strips
7. Test on macOS 13+ to verify full compatibility

## Files Affected

- `MatrixOpenGLView.h/.m` — Replace with MTKView subclass
- `MatrixView.m` — Rewrite all GL init/draw/resize methods
- `MatrixStrip.m` — Replace OpenGL array calls with Metal buffer calls
- `MatrixTexture.m` — Replace `glTexImage2D` with `MTLTexture`
- `GLUtils.m/.h` — Replace GL error checking with Metal error handling
- `MatrixMacros.h` — Update/remove GL-specific macros
