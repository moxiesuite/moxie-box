moxie-box
===========

Moxie Box management functionality.

Provides behavior for unboxing a new project from a predefined Moxie Box.


Box Configuration
-----------------

Moxie Boxes are configured via an optional `moxie-box.json` file in the
box repo's root directory.

This box configuration file specifies an object containing the following
properties:

- `ignore`

  A list of relative paths to files that should be removed upon box unpack.
  Useful to remove box READMEs or other artifacts that pertain to box but not
  the set-up Moxie project.

  Example:

  ```json
  "ignore": [
    "README.md",
    ".gitignore"
  ]
  ```

- `commands`

  An object mapping supported behaviors for project to invoked command strings.

  `moxie unbox` prints commands to screen upon unboxing for documentation
  purposes.

  Example:

  ```json
  "commands": {
    "compile": "moxie compile",
    "migrate": "moxie migrate",
    "test": "moxie test"
  }
  ```

- `hooks`

  An object to specify commands to run at particular steps in the unbox
  process. Maps strings identifying individual hooks to command strings.

  Example:

  ```json
  "hooks": {
    "post-unpack": "npm install"
  }
  ```


Available Unbox Hooks
---------------------

- `post-unpack`

  If provided, runs command after box files are fetched and cleaned up for a
  new project.

  Commonly useful to install dependencies, e.g.
