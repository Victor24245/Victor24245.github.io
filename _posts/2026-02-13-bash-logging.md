---
title: "Getting Started with Bash Logging"
date: 2026-02-13
categories:
  - DevOps
  - Bash
tags:
  - logging
  - bash
  - scripting
  - best-practices
toc: true
toc_label: "Contents"
toc_icon: "list"
header:
  teaser: /assets/images/bash-logging-teaser.jpg
excerpt: "Learn how to implement professional logging in your bash scripts with best practices and ready-to-use functions."
---

## Introduction

Logging is a critical aspect of any production script, yet it's often overlooked in bash scripting. In this post, I'll show you how to implement professional-grade logging in your bash scripts.

## Why Logging Matters

Good logging helps you:

1. **Debug Issues**: Quickly identify where things went wrong
2. **Monitor Performance**: Track execution time and bottlenecks
3. **Audit Actions**: Keep track of what scripts are doing
4. **Troubleshoot**: Understand the context when errors occur

## Basic Logging Function

Here's a simple but effective logging function you can use:

```bash
log() {
    local log_level=$1
    local message=$2
    local script_name=$(basename $0)
    local timestamp=$(date +"%Y-%m-%d %H:%M:%S")
    echo "$timestamp [$log_level] [$script_name] $message" | tee -a $LOGFILE
}
```

## Usage Example

```bash
#!/bin/bash

LOGFILE="/var/log/myscript.log"

# Source logging function (or define it in the script)
source logging.sh

# Use it in your script
log "INFO" "Script started"
log "WARN" "Disk space running low"
log "ERROR" "Failed to connect to database"
```

## Advanced Features

For production use, consider adding:

- **Log rotation**: Prevent log files from growing too large
- **Log levels**: Filter messages by severity
- **Timestamps**: Track when events occurred
- **Context**: Include function names and line numbers

## Conclusion

Implementing proper logging takes a bit of effort upfront, but it pays dividends when you need to troubleshoot issues in production. Start with the basic function above and expand as needed.

---

*Have questions or suggestions? Feel free to reach out!*
