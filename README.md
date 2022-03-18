# check-command-output-diff

## Description

An action to run a command and check the difference of the output of the command.

## Required input

1. command: Command to run.
1. command_output: Path of the command output file.
1. cache_key_prefix: Key prefix for cache of the command output file.

## Output

1. is_same: If old and new output is same, true.

## Example

```yaml
jobs:
  check:
    runs-on: ubuntu-latest
    steps:
      - run: echo 0 > ~/test
        shell: bash
      - uses: smilerobotics/actions-check-command-output-diff@v1
        id: compare
        with:
          command: 'echo 0'
          command_output: "~/test"
          cache_key_prefix: "test-is-same-${{ matrix.os }}"
      - run: echo ${{ steps.compare.outputs.is_same }}
        shell: bash
```
