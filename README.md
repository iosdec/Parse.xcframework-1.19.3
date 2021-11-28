# Parse / Bolts (1.19.3) .xcframework (iOS+simulator+osx)
Generated framework of iphoneos/iphone-simulator/osx architechtures for both Parse/Bolts frameworks.

### Why?

Compilation fails for a universal framework when building Parse/Bolts from the `Parse iOS SDK`. The ruby script manages to generate all valid architectures, but fails to combine them. These frameworks were combined with `xcodebuild -create-xcframework`:

```
xcodebuild -create-xcframework -framework build/Release-ios-iphoneos/Parse.framework -framework build/Release-ios-iphonesimulator/Parse.framework -framework build/Release-osx-macosx/Parse.framework -output Parse.xcframework
```
```
xcodebuild -create-xcframework -framework build/Release-ios-iphoneos/Bolts.framework -framework build/Release-ios-iphonesimulator/Bolts.framework -framework build/Release-osx-macosx/Bolts.framework -output Bolts.xcframework
```

### Build issues

You may experience issues related to `Undefined symbols ___llvm_profile_runtime` when building, this can be resolved by adding: `-fprofile-instr-generate` to `Build Settings > Linking > Other Linker Flags`.

You will also need to include these frameworks in your project:

```
AudioToolbox.framework
Foundation.framework
libiconv.tbd
libsqlite3.0.tbd
libz.tbd
Security.framework
```

Enjoy!
