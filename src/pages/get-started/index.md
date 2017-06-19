---
layout: main.html
---

# Getting started

First, install fuge via npm; globally.

```
npm install -g fuge
```

## A Micoservice shell?
Yup. Fuge is a shell environment that focuses on a specific system configuration, providing an emulation environment in which services can run in development that is close to a modern container production deployment.

## Usage
In order to run your system via fuge, you need to create a YAML configuration file. Fuge also integrates with docker-compose. Full documentation on configuring fuge is [available here](https://github.com/apparatus/fuge-config).

Full example demonstration systems are available here:
[https://github.com/apparatus/fuge-examples](https://github.com/apparatus/fuge-examples).

## Example Configuration
A simple configuration is provided below:

```
fuge_global:
  tail: true
  monitor: true
  monitor_excludes:
    - '**/node_modules/**'
    - '**/.git/**'
    - '*.log'
myservice:
  type: process
  path: ../myservice
  run: 'node index.js'
  ports:
    - myservice=8000
webapp:
  type: process
  path: ../webapp
  run: 'npm start'
  ports:
    - webapp=3000
mongo:
  image: mongo
  type: container
  ports:
    - mongo=27017:27017
```

This configuration defines a front end webapp process, a single microservice and a mongodb container. The system can be started by running:

```sh
$ fuge shell <path to config file>
fuge> start all
```

This will start the mongo container through the local docker API and also the webapp and myservice processes. Fuge will also inject configuration information into these processes as environment variables, tail the logs and watch the file system for changes, restarting the appropriate processes as you write code.

To fully explore the capabilites of Fuge, you are encouraged to run the example systems which can be found here: [https://github.com/apparatus/fuge-examples](https://github.com/apparatus/fuge-examples).

## Docker
Fuge is fully compatible with V1, V2 and V3 docker-compose formats. Fuge services can be specified entirely using docker-compose or entirely in fuge.yml or a mixture of anything in between.

## Command Reference
Fuge can be started by running:

```sh
$ fuge shell <path to fuge config file>
fuge>
```

The fuge command shell supports the following commands

| command       | action        |
| ------------- | ------------- |
| `help`  | display a list of supported commands |
| `ps` | list status of managed processes and containers |
| `info` [process] [full]`| show information on a specific process. The `full` option will output the entire environment that will be injected into this process|
| `start [process] / all` | start a process or all processes |
| `stop [process] / all` | stop a process and any associated watcher or all processes |
| `debug [process]` | start a process in debug mode (only supported for node.js processes) |
| `apply [Shell command]` | run the specified shell command in the root of each service e.g. `apply npm install`, `apply git status` |
| `zone` | display dns zone information for fuge internal DNS server - requires the `dns_enabled` setting in fuge configuration file |
| `watch [process] / all` | turn on watching for a process or for all processes |
| `unwatch [process] / all` | turn off watching for a process or for all processes |
| `tail [process] / all` | tail output for a process or for all processes |
| `untail [process] / all` | end tail output for a specific processes or for all processes |
| `grep 'search string' [process]` | searches a process' log or all processes' logs |
| `exit` | terminate all managed processes and exit the shell |

### Shell pass through
In addition to the above commands, Fuge will pass through all other commands to the underlying shell, for example:

```sh
fuge> ps aux | grep -i node
```

Will bypass the fuge ps command and execute the underlying `ps` command.

```sh
fuge> netstat -an | grep -i listen
```

Will be passed through to the underlying shell to display a lists of open listening port and so on.

## Contributing
The [apparatus team][] encourage open participation. If you feel you can help in any way, be it with
documentation, examples, extra testing, or new features please get in touch.

## License
Copyright the apparatus team 2016, Licensed under [MIT][].


