# nFin

A command line tool to give notifications on finish for long running commands.

## Description

Use this command line tool to receive a notification when the command finishes.
Set up a specific notification for when a command fails vs. succeeds.
Choose to receive notifications if the command took more than a certain amount of time to run or less than another amount of time to run.

## Installation

Run the following in your terminal

```shell
curl -s https://raw.githubusercontent.com/quinton22/nfin/main/bin/internal/install | bash
```

This will install the latest version of nfin, as well as set up nfin to run on every command in the terminal.
You can disable this feature in the config.

## Setup

_Development is still in progress, but for now:_

Set up the config.json file in the ~/.nfin directory. You can:

- Run `nfin -c settings` for an interactive setup
- Run `nfin -c <setting.separated.by.dots> <setting_value>` to set an individual setting value [\*\*](#still-under-development)

## Usage

There are multiple ways to use nFin:

### Automatic

Currently only supported for `zsh`

This is the default, any time a command is run in the terminal, if it takes longer than the configured amount of time, you will get a notification.

### Command line

There are multiple ways to run nFin on the command line.

1. Run your command preceded by `nfin`

   <pre>nfin <var>COMMAND</var></pre>

   <details open>
   <summary>Example</summary>
   Sleeps for 15 seconds, a notification will appear afterwards.

   ```sh
   nfin sleep 15
   ```

   </details>

2. If you have multiple commands separated by `;`, place your commands in quotes
   <pre>nfin "<var>COMMAND_1</var>[; <var>COMMAND_2</var>[; ...]]"</pre>

   <details open>
   <summary>Example</summary>
   Sleeps for 15 seconds, then runs `ls`, and a notification will appear afterwards.

   ```sh
   nfin "sleep 15; ls"
   ```

   </details>

   Do the same if you have multiple commands separated by `&&` or `||`

   <pre>nfin "<var>COMMAND_1</var> [{&& | ||} <var>COMMAND_2</var>[{&& | ||} ...]]"</pre>

   <details open>
   <summary>Example</summary>
   Sleeps for 15 seconds, then runs `ls`, and a notification will appear afterwards.

   ```sh
   nfin "sleep 15 && echo 'yay' || echo 'uh-oh'"
   ```

   </details>

3. Run your command followed by `; nfin`

   <pre><var>COMMANDS</var>; nfin</pre>
   <details open>
   <summary>Example</summary>

   ```sh
   pwd; nfin
   ```

   </details>

   By running this way, nfin will notify every time.

4. Run specific configuration [\*\*](#still-under-development)

## Configuration

The configuration is type defined in [config.type.json](/config/config.type.json)

<br>
<br>
<a name="still-under-development">** Still under development</a>
