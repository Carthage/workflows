# workflows
Opinionated workflows built on top of Carthage

## `carthage-developer-checkouts`

Replaces Carthage checkouts with symlinks pointed inside the parent directory
(`..`), useful for developing dependencies in coordination with the parent
project, while avoiding the need for submodules.

## `carthage-verify`

Verifies that the commitish values in the
[`Cartfile.resolved` file](https://github.com/Carthage/Carthage/blob/master/Documentation/Artifacts.md#cartfileresolved) are in sync with the commitish values in the
[`Carthage/Build/*.version` files](https://github.com/Carthage/Carthage/blob/master/Documentation/VersionFile.md).

Can be added to an Xcode project as a "run script" build phase to prevent
developers from building the project with carthage-built frameworks that are out
of sync with the contents of the `Cartfile.resolved`. This occurs because the
`Carthage/Build` folder is typically ignored in version control, and a developer
may have a stale contents in their local checkout from the last time they ran a
`carthage bootstrap`.

Similar in behavior to the CocoaPods [`Manifest.lock` file](https://www.objc.io/issues/6-build-tools/cocoapods-under-the-hood/#manifest-lock).
