---
title: "XFS Filesystem Corruption Recovery"
date: 2026-02-13
categories:
  - Linux
  - RHCSA
tags:
  - xfs_filesystem
  - grub
  - RHEL
  - best-practices
toc: true
toc_label: "Contents"
toc_icon: "list"
header:
  teaser: /assets/images/bash-logging-teaser.jpg
excerpt: "XFS doesn't shrink ❗❗❗"



---

So I just spent my afternoon recovering from what could've been a disaster if this wasn't a lab VM. 

Here's what happened: I was working with a RHEL 10 machine and decided to partition a 10GB XFS filesystem. Used `parted`, carved it in half, didn't think twice about it, and hit reboot.

Bad idea.

The system came back to a `grub>` prompt. No boot menu. Just errors about "unknown filesystem" everywhere I looked. All three partitions returning the same message. 

That sinking feeling hit - I'd corrupted the entire filesystem.

**What went wrong:**

Turns out XFS has a hard rule I should've remembered: **you can grow it, but you can never shrink it.** When I resized that partition smaller, the filesystem's superblock was still pointing to blocks that no longer existed. The transaction log was corrupted. Everything was pointing to nothing.

**The recovery:**

Booted from AlmaLinux rescue media and got to work:

- Ran `xfs_repair` - it complained about a corrupted log
- Had to use `xfs_repair -L /dev/vda3` to force log zeroing (this basically throws away any uncommitted transactions)
- Mounted the repaired filesystem - data was intact, thankfully
- Chrooted in and reinstalled GRUB
- Regenerated the boot config
- Crossed my fingers and rebooted

It worked. System's back up.

**The takeaway:**

Look, we all know the theory. But here's the reality: when you're moving fast in a lab environment, it's easy to forget the fundamentals. XFS doesn't shrink. Period. If you need a smaller partition, the only path is backup → destroy → recreate → restore.

Also, that `-L` flag in xfs_repair? It's a lifesaver when the log itself is toast, but it'll discard uncommitted changes. Use it knowing what you're giving up.

And honestly? I'm glad this happened in a VM. These mistakes in production are career-defining moments for all the wrong reasons.


#Linux #RHEL #SystemAdministration #XFS #DisasterRecovery #SysAdmin

---


