# nFin

A command line tool to give notifications on finish for long running commands.

## Description

Use this command line tool to receive a notification when the command finishes.
Set up a specific notification for when a command fails vs. succeeds.
Only receive a notification if the command took a configurable amount of time to fail or succeed.

## Installation

1. Run the following in your terminal
   `curl -s https://raw.githubusercontent.com/quinton22/nfin/main/bin/internal/install | bash`

## Setup

_Development is still in progress, but for now:_

Set up the config.json file in the ~/.nfin directory. You can:

1. Manually replace items in the config.json file directory
2. Run `nfin -c settings` for an interactive setup
3. Run `nfin -c <setting.separated.by.dots> <setting_value>` to set an individual setting value [\*\*](#still-under-development)

## Usage

There are multiple ways to use nFin:

### Automatic

Currently only supported for zsh

1. This is the default, any time a command is run in the terminal, if it takes longer than the configured amount of time, you will get a notification.

### Command line

1. Run your command preceded by `nfin`

```shell
nfin <your command here>
```

2. If you have multiple commands separated by `;`, place your commands in quotes

```shell
nfin "<first command>; <second command>"
```

Do the same if you have multiple commands separated by `&&` or `||`

```shell
nfin "<first command> && <second command> || <third command>"
```

3. Run your command followed by `; nfin`

```shell
<one or more semi-colon separated commands>; nfin
```

Running this way, does not conform to the delays set in the config and will always notify as successful.

4. Automatically run on every command by a configuration in the ~/.bashrc or ~/zshrc file [\*\*](#still-under-development)
5. Run specific configuration [\*\*](#still-under-development)

### Supported Configurations

```
{
  "settings": {
    "notification": {
      "onSuccess": { // on a successful command
        "enabled": boolean, // enabled or disabled
        "onTimeElapsed": boolean, // if true, will run only if "time" <= elapsed time to run the code
        "time": int, // time in seconds the code must run before notifying
        "type": "alert" | "bell" | "notification" // default is "bell", looking to add "email" and "text"
                                                  // "bell" uses the special character "\a"
                                                  // "alert" Mac only, will show a dismissable alert
                                                  // "notification" Mac only, will notify in the notification panel
      },
      "onError": { // on an unsuccessful command
        "enabled": boolean,
        "onTimeElapsed": boolean,
        "time": int,
        "type": "alert" | "bell" | "notification"
      }
    }
  }
}
```

<br>
<br>
<a name="still-under-development">** Still under development</a>
