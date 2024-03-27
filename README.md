# unified-project-tool

unified-project-tool is a simple tool to bootstrap projects.

The project is created from a template, and then a specific file can be bootstrapped with the needed arguments.

See the projects/ directory for some examples.

## Bootstrap files

Here is the general format for .bootstrap-args files:
```
#!/bin/bash
echo "<project type name>" "<bootstrapped file> <args: NAME=VALUE>"
```

Using bash here isn't a requirement, since the bootstrap file is run using `exec <name>.bootstrap-args` in the script.
(See [line 102 in the script](unified-project-tool#L102))

You could, for example, use python to provide the necessary arguments to unified-project-tool.

## Command usage

```
Usage: unified-project-tool [MODE] [PROJECT TYPE] [PROJECT NAME]
```

Use `unified-project-tool help` to show the following help message:

```
Usage: <executable path> [MODE] [PROJECT TYPE] [PROJECT NAME]

Modes:
- bootstrap: Bootstrap a project with the specified type and name
- install:   Install unified-project-tool to the paths defined by EXECUTABLE_INSTALL_DIR
             and PROJECTS_INSTALL_DIR (see defaults in the executable: <executable path>)
- help:      Show this help message

Available project types:
- cmake-c
- cmake-cpp

Unified project tool v1.0.0
Copyright (c) 2024 jarvarvarvis
```

If you add custom project types, they will be shown in the list.


Here is an example command: `unified-project-tool cmake-c my-project`

This will create a new project from the cmake-c template with the name "my-project" in the current directory.
