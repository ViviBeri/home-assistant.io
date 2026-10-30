---
title: "Automatic Home Assistant updates"
description: "Understand which Home Assistant updates install automatically, when they install, and how to pause or skip them."
---

Automatic Home Assistant updates can install eligible Home Assistant Core patch releases for you. This feature is available only on {% term "Home Assistant Operating System" %} installations using the stable update channel.

Automatic updates are limited to patch releases of your current major version. For example, if you run version 2026.10.1, Home Assistant can install a later 2026.10.x patch release automatically after the configured waiting period.

Automatic updates do not install:

- Major releases, such as an update from 2026.10.x to 2026.11.0.
- Home Assistant apps.
- Marketplace items.
- Home Assistant Operating System updates.
- Updates on {% term "Home Assistant Container" %} installations.
- Updates when using the beta or dev update channel.

You can continue to install these updates manually. For details, refer to [Updating Home Assistant, apps, and devices](/common-tasks/general/updating/).

## When automatic updates run

Home Assistant waits for the configured period after it first detects a patch release. The default waiting period is **3 days**.

The default installation window is **03:00 to 05:00**, using your Home Assistant instance's time zone. By default, this window is available every day of the week.

Home Assistant checks whether an update is eligible at startup and regularly afterwards. It installs no more than one version during a check, and only inside the configured time window. The installation restarts Home Assistant.

The waiting period, time window, and allowed weekdays can be configured. The available waiting periods are 0, 1, 3, 7, and 14 days.

## Pause or resume automatic updates

You can pause automatic updates without changing the configured schedule. Turn off the **Automatic Home Assistant updates** switch on the Home Assistant Core device to pause installations. Turn the switch on again to resume them.

Pausing automatic updates does not prevent you from installing an update manually.

## Skip a version

If you do not want a particular patch release to install automatically, skip that version from the Home Assistant Core update entity on the **Settings** > **System** > **Updates** page.

A skipped version remains excluded from automatic installation. Skipping a version does not prevent a newer patch release from being installed when it becomes eligible.

## Turn off automatic updates

To stop automatic Home Assistant updates, disable the automatic update setting. You can enable it again later. Turning off automatic updates does not remove available updates or prevent manual installation.

## If an automatic update fails

Home Assistant checks the result after it restarts.

If the update succeeds, Home Assistant records the successful update. If the update fails and Supervisor rolls it back, Home Assistant creates a repair issue explaining that the automatic update was undone. The failed version is not tried automatically again.

Review the repair issue before attempting to install that version manually. Supervisor may also provide details about the rollback.

## Backups

Automatic updates follow the same backup preference used by the Home Assistant update dialog. If backup before updating is enabled, Home Assistant creates a backup before installing the patch release. The configured automatic backup settings are used when available; otherwise, Home Assistant uses a local manual backup.

For general update instructions, including manual updates and app updates, refer to [Updating Home Assistant, apps, and devices](/common-tasks/general/updating/).
