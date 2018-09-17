# Pomogoro
golang implementation of a pomodoro cli tool

## Description

Pomogoro is a simple CLI tool written in go for managing Pomodoro timers, 
logging time recorded and summarizing timers by week.

### Desired Functionality

1. CLI timers set by config by default and overridden by CLI.
1. Config manipulation from file or CLI
1. Logging timers to file, google sheet, database?, other? only when timers complete.
1. Configurable Slack API interface to set `/dnd` when work starts and `/remind` when it ends

#### Timer Examples.

    - `pomogoro start -w`: starts a 25 min session defined in a config.
    - `pomogoro start -w -t 20`: starts a 20 minute session overriding config.
    - `pomogoro start -s`: starts a 5 minute (short) break defined in config.
    - `pomogoro start -s -t 10: starts a 10 minute (short) break overriding config.
    - `pomogoro start -l`: starts a 30 minute (long) break defined in config.
    - `pomogoro start -c`: starts a count-up timer from 00:00.
    - `pomogoro stop -w`, `pomogoro stop -s`, `pomogoro stop -l`: ends timer prematurely.
    - `pomogoro restart -w`, `pomogoro restart -s`, `pomogoro restart -l`: restarts timer.

#### Config Manipulation Examples.
    
    - `pomogoro set -w 20`: modifies the config file to set work timer default to 20 minutes.
    - `pomogoro set -s 10`: modifies the config file to set the short timer default to 10 minutes.
    - `pomogoro set -l 45`: modifies the config file to set the long timer default to 45 minutes.
    - `pomogoro load config_file.json`: redirects default config to a new file.
    - `pomogoro save config_file.json`: saves current config to file.
    - `pomogoro edit config`: opens the current default config file in the default editor (like git handles commit)
    - `pomogoro view config`: pretty prints current config content to STDOUT.

#### Example Config

```json

[
    {'work_time': 25,
     'short_break_time': 5,
     'long_break_time': 30,
     'logging_path': 'URL for google sheets minpulation or filepath for local json dump'
     }
]
```

#### Example Log

```json

[
    {'work_time_start': 'timestamp',
     'work_time_end': 'timestamp',
     'work_time_tags': ['project1', 'problem1'],
     'work_time_duration': 'integer'},
    {'short_break_start': 'timestamp',
     'short_break_end': 'timestamp'}
]
```
