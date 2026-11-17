# setup-icarus

This action downloads a prebuilt [Icarus Verilog](https://github.com/steveicarus/iverilog) from [daxzio/icarus-package](https://github.com/daxzio/icarus-package) and adds it to `PATH`. The job that uses it does not compile Icarus.

Supported runners: **Ubuntu 24.04** and **Ubuntu 26.04** (including **`ubuntu-latest`** while that label points at 26.04). By default the action downloads the tarball for the runner’s `VERSION_ID`.

```yaml
name: Check
on: [push, pull_request]
jobs:
  check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: daxzio/setup-icarus@v1
      - run: iverilog -V
```

The default `version` is the latest package release (`2026.11.04` devel snapshot unless you pin `v13_0`).

```yaml
- uses: daxzio/setup-icarus@v1
  with:
    version: "2026.11.04"
```

## Tags

| Tag | What it is |
|---|---|
| `2026.11.04` | Latest devel snapshot; assets for 24.04 and 26.04 |
| `v13_0` | Upstream stable 13.0 |