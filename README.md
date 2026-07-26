# envdiff

> "It works on that box." Here is the list of reasons why.

**Status:** 🚧 In development

## Overview

Compare environment between two hosts or containers - packages, kernel, env vars, locales, timezones - and show only the drift that could explain a bug.

## Features

- Collects packages (dpkg, rpm, apk), kernel and glibc version, sysctls, environment, locale and timezone
- Compares host to host over SSH, container to container, or a host against a container image
- Prints drift only, with an ignore file for the differences you have already accepted
- Ranks the drift that plausibly explains behaviour first: libc, OpenSSL, tzdata, locale collation, `ulimit`
- Snapshots to JSON so today's box can be diffed against last week's known-good one
- Agentless and read-only: one SSH session running read-only commands, nothing installed on the target

## Stack

Go + cobra, golang.org/x/crypto/ssh, the Docker Engine API client for container targets.

## Usage

```bash
envdiff hosts web-01 web-02 --only packages,env,sysctl --ignore-file .envdiffignore
```

## License

MIT
