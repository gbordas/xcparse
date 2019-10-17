# xcparse

A command line tool to extract code coverage & screenshots from Xcode 11 XCResult files.

To learn more about Xcode 11's xcresult format, read [Rishab Sukumar's post on the ChargePoint Engineering blog](https://www.chargepoint.com/engineering/xcparse/)

## Installation 

xcparse is installed via [Homebrew](https://brew.sh). Enter the following command in Terminal:

```
brew install chargepoint/xcparse/xcparse
```
This will tap into our xcparse Homebrew tap and install the tool on your local machine.

## Usage

```
xcparse <command> <options>
```

Below are a few examples of common commands. For further assistance, use the --help option on any command

### Screenshots

```
xcparse screenshots --os --model --test-run /path/to/Test.xcresult /path/to/outputDirectory
```

This will cause screenshots to be exported like so:

![Screenshots exported into folders](Docs/Images/screenshots_options_recommended.png?raw=true)

Options can be added & remove to change the folder structure used for export.  Using no options will lead to all attachments being exported into the output directory.

### Attachments

```
xcparse attachments /path/to/Test.xcresult /path/to/outputDirectory --uti public.plain-text public.image
```

Export all attachments in the xcresult that conform to either the ```public.plan-text``` or the ```public.image``` uniform type identifiers (UTI). The screenshots command, for example, is actually just the attachments command operating a whitelist for ```public.image``` UTI attachments.  Other common types in xcresults are ```public.plain-text``` for debug descriptions of test failures.

Read [this Apple documentation]((https://developer.apple.com/library/archive/documentation/Miscellaneous/Reference/UTIRef/Articles/System-DeclaredUniformTypeIdentifiers.html#//apple_ref/doc/uid/TP40009259-SW1)) for a list of publicly documented UTIs.

### Code Coverage

```
xcparse codecov /path/to/Test.xcresult /path/to/exportCodeCoverageFiles
```

This will export the action.xccovreport & action.xccovarchive into your output directory.

### Logs

```
xcparse logs /path/to/Test.xcresult /path/to/exportLogFiles
```

### Help

```
xcparse --help

xcparse screenshots --help
```

Learn about all the options we didn't mention with ```--help```!

## Modes

### Static Mode
This is the default mode in which xcparse runs if the user specifies a command & arguments.

### Interactive Mode
When the user runs xcparse with no arguments, xcparse runs in interactive mode. In this mode the user is prompted to enter commands and arguments as required.

## Useful Commands

1. brew untap - Untaps from specified homebrew tap
2. brew uninstall - Uninstall homebrew tool
