title: Commands
---

Pandora.js provides CLI commands for application management. They are listed below:

- init
- start
- stop
- restart
- list
- log
- ps
- exit
- dev

## init - Initiate a Pandora.js project

```bash
pandora init <filePath> --name customName
```
Generate a `procfile.js`.

1. `<filePath>` required, the file path of the entry file.
2. `--name` optional, the process name for the fork mode.

Example:

```bash
$ pandora init ./app.js
? Which type do you like to generate ? (Use arrow keys)
❯ fork 
  cluster 
** A newly generated procfile.js could be found under current directory. **
```
## start - Start an application in the background

```bash
pandora start [path] --name urAppName --env="NODE_ENV=production" --node-args="--expose-gc"
```

Frequently used arguments:

1. `[path]` Required, project directory, using the working directory by default.
2. `--name=urAppName` Optional, to specify the name of current application. Use the name defined in package.json by default or the current directory name.
3. `--env="NODE_ENV=production"` Optional, to specify the environmental variables. The settings could be retrieved via `process.env` in application.
4. `--node-args="--expose-gc"` Optional, to specify the runtime arguments.
5. `--args="--a=b"` Optional, to specify the application arguments.

Example:

```bash
# e.g. '/home/admin/mytaobao/target/mytaobao' is the working directory, and name property in package.json is not defined.

pandora start # Start application, using the default app name via directory name: mytaobao. work the same as --name=mytaobao
pandora start . --name mytaobao # Work the same as command above
pandora start `pwd` # Work the same as command above
```

## stop - stop an application

> Notice: Only applications launched by `start` command can be stopped by this command

```bash
pandora stop [appName]
```

This stops an application.

1. `[appName]` Optional, to specify the name of current application.  Use the name defined in package.json by default or the current directory name.

Example:

```bash
pandora stop mytaobao # Here 'mytaobao' is the application name.
```

## restart - Restart an application

```bash
pandora restart [appName]
```

Equals to `pandora stop` and then `pandora start`.


1. `[appName]` Optional, to specify the name of current application.  Use the name defined in package.json by default or the current directory name.

Example:

```bash
pandora restart mytaobao # Here 'mytaobao' is the application name.
```

## list - List all running applications

> Notice: applications launched via `pandora dev` is not guarded by daemon process, thus won't be listed by this command.

```bash
pandora list
```

List all running applications:

![list](https://img.alicdn.com/tfs/TB107mPeOqAXuNjy1XdXXaYcVXa-2646-330.png) 


## log - View logs

```bash
pandora log [appName] --follow --lines --full --daemon
```

1. `[appName]` Optional, to specify the name of current application.  Use the name defined in package.json by default or the current directory name.
2. `--follow` Optional, alias as  `-f`, work the same as `tail -f`.
3. `--lines` Optional, alias as `-l`, output the last few lines of logs, by default display last 50 lines.
4. `--full` Optional, output all logs.
5. `--daemon` Optional, output logs of the daemon process.

## ps - View processes tree

```bash
pandora ps <appName>
```

1. `<appName>` Required, the name of the application.


## exit - Quit the Pandora.js

Stop all running applications and quit pandora.js daemon process.

```bash
pandora exit
```

## dev - Start an application in the foreground

> Notice: `pandora dev` would not launch the daemon process, thus the launched application won't be listed in the output of `pandora list`.

```bash
pandora dev [path] --name urAppName --env="NODE_ENV=production" --node-args="--expose-gc"
```

Start an application in the foreground, without the guardianship of daemon process, logs output to stdout directly.
It is mostly used for local development and debugging. It accepts the same parameters as the `start` command.

1. `[path]` Required, project directory, using the working directory by default.
2. `--name=urAppName` Optional, to specify the name of current application. Use the name defined in package.json by default or the current directory name.
3. `--env="NODE_ENV=production"` Optional, to specify the environmental variables. The settings could be retrieved via `process.env` in application.
4. `--node-args="--expose-gc"` Optional, to specify the runtime arguments.
5. `--args="--a=b"` Optional, to specify the application arguments.