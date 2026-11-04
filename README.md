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

Pin a release with `version`. Use the upstream tag, including the `v`. The default is the latest package release.

```yaml
- uses: daxzio/setup-icarus@v1
  with:
    version: "v13_0"
```
