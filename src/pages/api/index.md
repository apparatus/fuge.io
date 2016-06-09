---
layout: main.html
---

# API reference


## Help [Command...]
- __Command:__ - name of the command that help is needed with.

The help command prints out the available options, usage and syntax of the specified `Command`.

___Example: send___
```bash
? fuge> help send
  Usage: send [options] <process> <message>
  sends a message to a specific process
  Options:
    --help  output usage information
```

## Ps
List status of managed processes and containers.

## Proxy
List proxy and port forwarding status.

## Info [Process]
- __Process:__ - name of the process to be requested.

List environment block injected into each process.

___Example: info service1___
```bash
running:  PROXY_HOST=127.0.0.1 SERVICE_HOST=0.0.0.0 frontend_PORT=10000 api_PORT=10001 service1_PORT=10002 service2_PORT=10003 SERVICE_PORT=20000  exec /Users/shanelacey/.nvm/versions/node/v4.2.4/bin/node -r /Users/shanelacey/Documents/fuge/fuge.js index.js
command: /Users/shanelacey/.nvm/versions/node/v4.2.4/bin/node -r /Users/shanelacey/Documents/fuge/fuge.js index.js
directory: /Users/shanelacey/Documents/test/fuge/site
environment:
  PROXY_HOST=__TARGETIP__
  SERVICE_HOST=0.0.0.0
  frontend_PORT=10000
  api_PORT=10001
  service1_PORT=10002
  service2_PORT=10003
  SERVICE_PORT=20000
```

## Stop [Process...]
- __Process:__ - name of the process to be stopped.

Stop a process.

___Example: stop service1___
```bash
? fuge> stop service1
stopping: service1
sending SIGKILL to  parent process: 7865
process exit [7865]: service1
```

Process names can be chained as shown in example 2.

___Example 2: stop service1 service2___
```bash
? fuge> stop service1 service2
stopping: service1
stopping: service2
sending SIGKILL to  parent process: 8161
sending SIGKILL to  parent process: 8165
process exit [8161]: service1
process exit [8165]: service2
```

__Note:__ ___Using 'stop' or 'stop all' without providing a process name kills all processes.___

## Start [Process...]
- __Process:__ - name of the process to be started.

Start a process.

___Example: start service1___
```bash
? fuge> start service1
running: service1
running:  PROXY_HOST=127.0.0.1 SERVICE_HOST=0.0.0.0 frontend_PORT=10000 api_PORT=10001 service1_PORT=10002 service2_PORT=10003 SERVICE_PORT=20002  exec /Users/shanelacey/.nvm/versions/node/v4.2.4/bin/node -r /Users/shanelacey/Documents/fuge/fuge.js service.js
```

Process names can be chained as shown in example 2.

___Example 2: start service1 service2___
```bash
? fuge> start service1 service2
running: service1
running:  PROXY_HOST=127.0.0.1 SERVICE_HOST=0.0.0.0 frontend_PORT=10000 api_PORT=10001 service1_PORT=10002 service2_PORT=10003 SERVICE_PORT=20002  exec /Users/shanelacey/.nvm/versions/node/v4.2.4/bin/node -r /Users/shanelacey/Documents/fuge/fuge.js service.js
running: service2
running:  PROXY_HOST=127.0.0.1 SERVICE_HOST=0.0.0.0 frontend_PORT=10000 api_PORT=10001 service1_PORT=10002 service2_PORT=10003 SERVICE_PORT=20003  exec /Users/shanelacey/.nvm/versions/node/v4.2.4/bin/node -r /Users/shanelacey/Documents/fuge/fuge.js service.js
```

__Note:__ ___Using 'start' or 'start all' without providing a process name starts all processes.___

## Debug [Process]
- __Process:__ - name of the process to be debugged.

Start a process in debug mode and launch node-debug.

___Example: debug service1___
```bash
? fuge> debug service1
running: service1
running:  PROXY_HOST=127.0.0.1 SERVICE_HOST=0.0.0.0 frontend_PORT=10000 api_PORT=10001 service1_PORT=10002 service2_PORT=10003 SERVICE_PORT=20002  exec node-debug -d 5858 -p 8080 service.js
```

## Profile [Process]
- __Process:__ - name of the process to be profiled.

Start a process with 0x, when the process is stopped a flamegraph will be generated in the services folder.

## Watch [Process]
- __Process:__ - name of the process to be watched.

Turn on watching for a process or for all processes.

___Example: watch service1___
```bash
? fuge> watch service1
watching: service1
```

__Note:__ ___Using 'watch' or 'watch all' without providing a process name starts watching for all processes.___

## Unwatch [Process]
- __Process:__ - name of the process to be unwatched.

Turn off watching for a process or for all processes.

___Example: unwatch service1___
```bash
? fuge> unwatch service1
un-watching: service1
```

__Note:__ ___Using 'unwatch' or 'unwatch all' without providing a process name stops watching for all processes.___

## Tail [Process]
- __Process:__ - name of the process to be tailed.

Tail output for a process or for all processes.

__Note:__ ___Using 'tail' or 'tail all' without providing a process name starts tailing for all processes.___

## Untail [Process]
- __Process:__ - name of the process to be untailed.

Stop tailing output for a process or for all processes.

__Note:__ ___Using 'untail' or 'untail all' without providing a process name stops tailing for all processes.___

## Grep 'search string' [Process]
- __'search string'__ - string to be searched for.
- __Process:__ - name of the process to be searched.

Searches a process' log or all processes' logs.

__Note:__ ___Using 'grep "search string"' or 'grep "search string" all' without providing a process name searches all processes.___

## Exit
Terminate all managed processes and exit.

__Note:__ ___'quit' is also accepted.___
