# GitHub Estimates Action

Automatically update GitHub projects description with total estimate (i.e. story points, hours, etc.) of each project column, for quick overview.

## Inputs

### `who-to-greet`

**Required** The name of the person to greet. Default `"World"`.

## Outputs

### `time`

The time we greeted you.

## Example usage

uses: actions/hello-world-javascript-action@v1
with:
  who-to-greet: 'Mona the Octocat'

on:
  issues:
    types: [labeled, unlabeled]
  project_card:
    types: [moved, created]
