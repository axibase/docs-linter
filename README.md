# docs-linter
Github Action to setup static analysis in Axibase documentation repositories

Example workflow

```yml
name: Docs Linter

on:
  push:
    branches: [ master ]
  pull_request:
  schedule:
    - cron: "0 3 * * *"

jobs:
  lint:
    runs-on: ubuntu-latest
    strategy:
      fail-fast: false
      matrix:
        linter: [links, spelling, style, anchors]

    steps:
      - uses: actions/checkout@v2
        with:
          fetch-depth: 0
      - name: Running ${{ matrix.linter }} linter
        uses: axibase/docs-linter@v1
        with:
          linter: ${{ matrix.linter }}
```

