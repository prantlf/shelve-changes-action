# Shelve Changed Files

GitHub action for storing modified files to cache, to be restored by [unshelve-changes-action] in another job later.

Uses git to detect changed files.

## Usage

Store the modified files to cache:

```yml
- uses: prantlf/shelve-changes-action@v1
```

Store only some of the modified files to cache, if there're more modified on the disk:

```yml
- uses: prantlf/shelve-changes-action@v1
  with:
    add-modified: false
    add-extra: |
      package.json
      CHANGELOG.md
```

## Inputs

The following parameters can be specified using the `with` object:

### branches

Type: `String`<br>
Default: `'main master'`

Branches which this action should run for, which are used to publishing releases. Use whitespace for separating the branch names. If you want to use multiple lines in YAML, introduce them with ">-". If you want to allow all branches, set the value to "*".

### enable

Type: `Boolean`<br>
Default: `true`

Can be set to `false` to prevent this action from running. It's helpful in the pipeline, which will not continue releasing, but only building and testing, and that will be decided in the middle of a job execution.

### add-modified

Type: `Boolean`<br>
Default: `true`

Can be set to `false` to prevent modified files from adding to the cache.

### add-new

Type: `Boolean`<br>
Default: `false`

Can be set to `true` to add also newly created files to the cache.

### add-extra

Type: `String`<br>

Additional files for putting to cache by this action, separated by spaces. They should not be picked by `add-modified` or `add-new` to avoid duplicates in the final list.

## Outputs

The following parameters can be accessed by the `github` context:

### stored

Type: `Boolean`<br>

Set to `true` if the files were stored to cache.

### files

Type: `String`<br>

Files put by this action to cache, separated by spaces.

### cache-key

Type: `String`<br>

The key, which was used to store the files to cache.

## License

Copyright (C) 2023-2024 Ferdinand Prantl

Licensed under the [MIT License].

[MIT License]: http://en.wikipedia.org/wiki/MIT_License
[unshelve-changes-action]: https://github.com/prantlf/unshelve-changes-action
