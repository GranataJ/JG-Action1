# JG Random Number Generator

A composite GitHub Action that generates a random integer in an inclusive range.

## Usage

```yaml
- name: Generate a random number
  id: random
  uses: GranataJ/JG-Action1@v1
  with:
    min: 1
    max: 100

- name: Use the generated number
  run: echo "Generated number: ${{ steps.random.outputs.generated-number }}"
```

## Inputs

| Input | Required | Default | Description |
| --- | --- | --- | --- |
| `min` | No | `1` | Inclusive minimum value. Must be between `0` and `32767`. |
| `max` | No | `100` | Inclusive maximum value. Must be between `min` and `32767`. |

## Output

| Output | Description |
| --- | --- |
| `generated-number` | The generated integer within the requested range. |

The action uses Bash's `$RANDOM` source and rejection sampling to avoid modulo bias. Inputs outside the supported range, or where `min` is greater than `max`, fail with an error.

## Publishing

Create a version tag and GitHub release (for example, `v1.0.0`), then select the option to publish the release to GitHub Marketplace. Consumers can use the major-version tag, such as `@v1`.
