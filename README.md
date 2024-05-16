# MoltenVK builds compatible with osxcross

Official Khronos [MoltenVK releases](https://github.com/KhronosGroup/MoltenVK/releases/)
are incompatible with current osxcross versions due to Xcode automatically
using the `-fobjc-msgsend-selector-stubs` optimization.

The linker used by osxcross doesn't seem to support these yet, even when
compiling against Apple LLVM.

See this upstream issue for details:
- https://github.com/KhronosGroup/MoltenVK/issues/1756

This repository simply does it own builds of MoltenVK with these flags added to
disable the optimization:

```
-fno-objc-msgsend-selector-stubs -Wno-unused-command-line-argument
```

That's the only difference with Khronos' builds.
