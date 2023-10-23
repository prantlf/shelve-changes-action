# Shelve Changed Files

GitHub action for storing modified files to cache, to be restored by [unshelve-changes-action] in another job later.

Uses git to detect changed files.

## Usage

Store the modified files to cache:

```yml
- uses: prantlf/shelve-changes-action@v1
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

Copyright (C) 2023 Ferdinand Prantl

Licensed under the [MIT License].

[MIT License]: http://en.wikipedia.org/wiki/MIT_License
[unshelve-changes-action]: https://github.com/prantlf/unshelve-changes-action
