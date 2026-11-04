# setup-icarus

This action downloads a prebuilt [Icarus Verilog](https://github.com/steveicarus/iverilog) from [daxzio/icarus-package](https://github.com/daxzio/icarus-package) and adds it to `PATH`. The job that uses it does not compile Icarus.

Supported runner: `ubuntu-24.04` / `ubuntu-latest`.

```yaml
name: Check
on: [push, pull_request]
jobs:
  check:
    runs-on: ubuntu-24.04
    steps:
      - uses: actions/checkout@v4
      - uses: daxzio/setup-icarus@v1
      - run: iverilog -V
```

The default `version` is the latest package release. Right now that is `2026.11.04`, built from the `master` tip on that day. `iverilog -V` reports `14.0 (devel) (2026.11.04-dirty)`. Pin `v13_0` for the stable release.

```yaml
- uses: daxzio/setup-icarus@v1
  with:
    version: "2026.11.04"
```

## Tags

| Tag | What it is |
|---|---|
| `2026.11.04` | Latest. `master` at the end of that day. `iverilog -V` reports `14.0 (devel) (2026.11.04-dirty)`. |
| `v13_0` | Upstream stable 13.0. `-V` reports `13.0 (stable) (v13_0-dirty)`. |
