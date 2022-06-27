# Overview
macOS applications are required to be signed and notarized in order to comply with Gatekeeper.

* Get an Apple developer account & Developer ID Application certificate
* Sign the application and disk image
* Submit the disk image to Apple's notary service and staple the ticket to the disk image

# Get an Apple Developer Account & Developer ID Application Certificate

# Sign the Application & Disk Image

A typical macOS application may have only a few simple elements in the application bundle that require signing and a simple codesign command may be possible. However, in Spyder's circumstance, many dynamic libraries, frameworks, nested applications, and executables are packaged with the application bundle. These must all be (re)signed in order for the application to be accepted by the notary service.

Signing all the elements in the application bundle must be done from the inside-out, i.e. executables inside a nested application or framework must be signed first, then the containing application or framework must also be signed. For Spyder, there are a few primary elements to pay attention to.
* Qt frameworks
* Executables and dynamic libraries (`.so`, `.dylib`) in the `Spyder.app/Contents/Resources` and `Spyder.app/Contents/Frameworks`
* Python framework
* Top level application executables in `Spyder.app/Contents/MacOS`

All signatures must include a secure timestamp (`--timestamp` option). Applications, frameworks, and some executables must additionally have hardened runtime enabled (`--options runtime` option). Ultimately, however, the notary service log will provide a definitive list of which files are missing signatures and how they should be signed. This guide guide was produced by trial-and-error to determine which files in the Spyder required signatures and how they needed to be signed. This means that some adjustments to the signing procedure for Spyder may be required in the future if Spyder's internal packages are changed.

## Qt frameworks

These frameworks reside in `Spyder.app/Contents/Resources/lib/python<ver>/PyQt5/Qt5/lib/`. Each `*.framework` in the directory requires the executables contained therein to be signed with

    $ codesign --timestamp --sign <CERTID> <FILE>

after which the `*.framework` is signed with

    $ codesign --timestamp --sign <CERTID> --options runtime <FILE>

There is an exception for `QtWebEngineCore.framework` which has an additional nested application, `QtWebEngineCore.framework/Helpers/QtWebEngineProcess.app`, requiring hardened runtime enabled.

## Executables and dynamic libraries

Executables and dynamic libraries (`.so`, `.dylib`) in the `Spyder.app/Contents/Resources` and `Spyder.app/Contents/Frameworks` directories require the standard codsign.

    $ codesign --timestamp --sign <CERTID> <FILE>

Some dynamic libraries reside in `Spyder.app/Contents/Resources/python<ver>.zip`. In order to sign these, the zip archive must be extracted, the files signed, and then the contents re-archived. However, in order for the signatures to survive the archive process (meta-data included) `ditto` must be used rather than the standard `zip` tool.

    $ unzip <zipfile> <tempdir>
    $ <do the signing process here>
    $ ditto -c -k <tempdir> <zipfile>

## Python framework

The `Spyder.app/Contents/Frameworks/Python.framework`, like the Qt frameworks above, requires hardened runtime enabled, but does not require signing anything nested therein.

    $ codesign --timestamp --sign <CERTID> --options runtime Spyder.app/Contents/Frameworks/Python.framework

## Top level application executables

The top level application executables in `Spyder.app/Contents/MacOS`, followed by the application bundle itself, need to be signed with hardened runtime enabled.

    $ codesign --timestamp --sign <CERTID> --options runtime Spyder.app/Contents/MacOS/python
    $ codesign --timestamp --sign <CERTID> --options runtime Spyder.app/Contents/MacOS/Spyder
    $ codesign --timestamp --sign <CERTID> --options runtime Spyder.app

This completes the code signing process for the Spyder application bundle.

# Submit the Disk Image to the Notary Service and Staple the Ticket
