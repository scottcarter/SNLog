
## About

SNLog is a lightweight Swift logger with support for Issue Navigator flagging.

### What is Issue Navigator flagging?

With Objective-C, I was able to insert pragma flags (messages) into the Issue Navigator.   I used this to 
allow me to find FIXME markers in my code as well as temporary log messages.  This was implemented with 
a set of macros that I maintained in a common header file.   

Unfortunately Swift does not support general preprocessing of the code, so pragma flags and macros are not an option
in Swift.

SNLog provides an alternative by making use of a benign warning:
"Treating a forced downcast to '<custom class>' as optional will never produce 'nil'"

## Screenshot

![example1 img](SNLog_screenshot_1.png?raw=true)


## Features

* Easily insert log messages that include the file, function and line number where invoked.
* Calls to SNLog can optionally appear in the Issue Navigator for temporary log messages (allows you to find them easily).
* Insert one line Fixme statements that appear in the Issue Navigator (without log).


## Installation

Download and add SNLog.swift to your project (CocoaPods does not currently provide support for Swift).

If your code currently uses any of the following global variables then you will need to rename them in SNLog.swift

```
g_log
g_fixme
g_anyFixme
```

## Usage

### Simple logging

```
SNLog.log("<message>")
SNLog.info("<message>")
SNLog.error("<message>")
```

### Log with Issue Navigator flag

```
g_log = SNLog.log("<message>") as SNLog
g_log = SNLog.info("<message>") as SNLog
g_log = SNLog.error("<message>") as SNLog
```

### Need to return Void from a function after logging?

```
SNLog.info("<message>")
Void()
```

### Insert a Fixme line with Issue Navigator flag

```
g_fixme = g_anyFixme as SNLog.Fixme
```

## Author

Scott Carter

## License

SNLog is available under the MIT license. See the LICENSE file for more info.

