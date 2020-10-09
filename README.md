Logger - Logging singleton for Godot Engine
===========================================

The *Logger* class is a GDScript singleton that provides a logging API for
projects developed with [Godot Engine](https://godotengine.org).

Usage
-----

Copy the `logger.gd` file into your project folder, and define it as an autoloaded
singleton in your project's settings (e.g. with the name *Logger*):
```
Logger="*res://logger.gd"
```

The methods of the API can then be accessed from any other script via the *Logger*
singleton:
```
  Logger.warn('alpaca mismatch!')
  Logger.info('reticulating splines...', mymodule)
```

Read the code for details about the API, it's extensively documented.

## Timestamp and log format
All logging levels include an timestamp, which will be formated acording to the date_time template in the Module.

Also the log format can be changed based on the keywords in the `FORMAT_IDS` dictionary.

### Formatting fields
**Timestamp fields**:
* yyyy = Year
* mm = Month
* dd = Day
* hh = Hour
* MM = Minutes
* ss = Seconds

**Log format fields**:
* {LVL}  = Level of the log
* {MOD}  = Module that does the logging
* {MSG}  = Message from the user
* {TIME} = Timestamp when the logging occurred

### Example:
```gdscript
Logger.get_module("main").time_template = "dd.mm.yyyy hh:MM:ss"
Logger.error(msg)

Logger.get_module("main").time_template = "hh:MM:ss"
Logger.error(msg)

Logger.output_format = "[{LVL}] {MSG} at {TIME}"
Logger.error(msg)
```
Results in: \
![Different log formats](/img/log_formating.png)





Licensing
---------

The Logger class and all other files of this repository are distributed under the
MIT license (see the LICENSE.md file).
