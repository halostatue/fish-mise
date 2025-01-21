# halostatue/fish-mise

A mostly unopinionated [fish shell][fish shell] plugin for [mise][mise].

This plugin is _not required_ with Homebrew mise, because it installs a default
activation script in `vendor_conf.d`. To prevent conflicts, however, this plugin
will disable the default activation script.

In addition to activating mise, possibly with options (described) below, this
plugin also enables completions. If it finds an existing mise completion, it
will ensure that `usage` is installed (with `mise -g usage`). If an existing
completion is not found and `usage` is found, `mise completion fish` is used.

## Options

### Activation

Mise activation can be adjusted with the universal variable
`$mise_activate_mode`, which recognizes one of two special values: can be set to
one of two values to adjust mise activation. These options are not able to be
used together.

- `shims`: This runs `mise activate --shims`, which is the same as setting
  `set -gx PATH $HOME/.local/share/mise/shims $PATH`.

  Choose this with: `set -U mise_activate_mode shims`.

- `status`: This runs `mise activate --status`, which prints the enabled tools
  and their versions when the directory changes. If you have many global tools
  installed, this output will be truncated.

  Choose this with: `set -U mise_activate_mode status`.

To return to standard mode, remove the variable with
`set -eU mise_activate_mode`.

### Completions

Mise completions behaviour can be disabled with `set -U mise_completions 0`.

## Installation

Install with [Fisher][fisher]:

```fish
fisher install halostatue/fish-mise@v1
```

### System Requirements

- [fish][fish] 3.0+

## Functions

### fish-mise

```fish
$ fish-mise example
example output
```

## Licence

[MIT](LICENCE.md)

[fish shell]: https://fishshell.com 'friendly interactive shell'
[fisher]: https://github.com/jorgebucaran/fisher
[fish]: https://github.com/fish-shell/fish-shell
[mise]: https://mise.jdx.dev
