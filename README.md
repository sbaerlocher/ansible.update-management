# Ansible Role: update-management

[![Build Status](https://travis-ci.org/sbaerlocher/ansible.update-management.svg?branch=master)](https://travis-ci.org/sbaerlocher/ansible.update-management) [![license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://sbaerlo.ch/licence) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-update--management-blue.svg)](https://galaxy.ansible.com/sbaerlocher/update_management)

## Description

Manage the update settings on Debian/Ubuntu, CentOS and Windows systems.

## Installation

```bash
ansible-galaxy install sbaerlocher.update_management
```

## Requirements

None

## Role Variables

### CentOS

| Variable                                  | Default           | Comments (type) |
| :---------------------------------------- | :---------------- | :-------------- |
| update_management_CentOS_enable           | true              |                 |
| update_management_update_cmd.hourly       | 'security'        |                 |
| update_management_update_cmd.daily        | 'default'         |                 |
| update_management_update_messages.hourly  | 'no'              |                 |
| update_management_update_messages.daily   | 'yes'             |                 |
| update_management_download_updates.hourly | 'no'              |                 |
| update_management_download_updates.daily  | 'yes'             |                 |
| update_management_apply_updates.hourly    | 'no'              |                 |
| update_management_apply_updates,daily     | 'no'              |                 |
| update_management_random_sleep.daily      | 360               |                 |
| update_management_random_sleep.hourly     | 15                |                 |
| update_management_system_name             | None              |                 |
| update_management_emit_via                | stdio             |                 |
| update_management_output_width            | 80                |                 |
| update_management_email_from              | root@localhost    |                 |
| update_management_email_to                | root              |                 |
| update_management_email_host              | localhost         |                 |
| update_management_group_list              | None              |                 |
| update_management_group_package_types     | mandatory,default |                 |
| update_management_debuglevel              | "-2"              |                 |
| update_management_mdpolicy                | "group:main"      |                 |

### Debian / Ubuntu

| Variable                                      | Default | Comments (type)                                               |
| :-------------------------------------------- | :------ | :------------------------------------------------------------ |
| update_management_Debian_enable               | true    |                                                               |
| update_management_UpdatePackageLists          | 1       | Do "apt-get update" automatically every n-days (0=disable)    |
| update_management_DownloadUpgradeablePackages | 0       | Do "apt-get upgrade --download-only" every n-days (0=disable) |
| update_management_AutocleanInterval           | 7       | Do "apt-get autoclean" every n-days (0=disable)               |
| update_management_CleanInterval               | 7       | Do "apt-get clean" every n-days (0=disable)                   |
| update_management_Verbose                     | 0       |                                                               |
| update_management_Package_Blacklist           |         |                                                               |
| update_management_AutoFixInterruptedDpkg      | true    |                                                               |
| update_management_MinimalSteps                | false   |                                                               |
| update_management_InstallOnShutdown           | false   |                                                               |
| update_management_Mail                        | false   |                                                               |
| update_management_MailOnlyOnError             | false   |                                                               |
| update_management_Remove_Unused_Dependencies  | false   |                                                               |
| update_management_Automatic_Reboot            | false   |                                                               |
| update_management_Automatic_Reboot_Time       | false   |                                                               |
| update_management_IgnoreAppsRequireRestart    | false   |                                                               |
| update_management_Dpkg_Options                | []      |                                                               |
| update_management_Dl_Limit                    | 70      |                                                               |

### Windows

| Variable                                              | Default | Comments (type)                                                                                                                                                                                            |
| :---------------------------------------------------- | :------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| update_management_GPO_enable                          | false   | If the updates are regulated by GPO, then set to true                                                                                                                                                      |
| update_management_Windows_enable                      | true    |                                                                                                                                                                                                            |
| update_management_SetActiveHours_enabled              | true    | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::ActiveHours)                                    |
| update_management_ActiveHoursStart                    | "8"     | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::ActiveHours)                                    |
| update_management_ActiveHoursEnd                      | "17"    | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::ActiveHours)                                    |
| update_management_NoAutoUpdate_enable                 | false   | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::AutoUpdateCfg)                                  |
| update_management_ScheduledInstallDay                 | 6       | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::AutoUpdateCfg)                                  |
| update_management_ScheduledInstallTime                | 17      | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.CloudContent::DisableWindowsSpotlightWindowsWelcomeExperience) |
| update_management_ScheduledInstallEveryWeek           | 1       | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::AutoUpdateCfg)                                  |
| update_management_AllowMUUpdateService                | 1       | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::AutoUpdateCfg)                                  |
| update_management_SetAutoRestartNotificationDisable   | 1       | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::AutoRestartNotificationDisable)                 |
| update_management_IncludeRecommendedUpdates           | 1       | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::IncludeRecommendedUpdates_Title)                |
| update_management_AutoRestartDeadlinePeriodInDays     | 3       | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::AutoRestartDeadline)                            |
| update_management_SetAutoRestartDeadline              | 1       | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::AutoRestartDeadline)                            |
| update_management_DetectionFrequencyEnabled           | 1       | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::DetectionFrequency_Title)                       |
| update_management_DetectionFrequency                  | 16      | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::DetectionFrequency_Title)                       |
| update_management_SetEngagedRestartTransitionSchedule | 1       | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::EngagedRestartTransitionSchedule)               |
| update_management_EngagedRestartTransitionSchedule    | 7       | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::EngagedRestartTransitionSchedule)               |
| update_management_EngagedRestartSnoozeSchedule        | 1       | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::EngagedRestartTransitionSchedule)               |
| update_management_EngagedRestartDeadline              | 14      | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::EngagedRestartTransitionSchedule)               |
| update_management_SetDisableUXWUAccess                | 1       | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::DisableUXWUAccess)                              |
| update_management_DeferFeatureUpdates                 | 1       | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::DeferFeatureUpdates)                            |
| update_management_BranchReadinessLevel                | 32      | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::DeferFeatureUpdates)                            |
| update_management_DeferFeatureUpdatesPeriodInDays     | 0       | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::DeferFeatureUpdates)                            |
| update_management_PauseFeatureUpdatesStartTime        | ""      | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::DeferFeatureUpdates)                            |
| update_management_Noincludedrivers_enable             | false   | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::ExcludeWUDriversInQualityUpdate)                |
| update_management_UseWUServer_enable                  | false   | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::CorpWuURL)                                      |
| update_management_WUServer                            | ""      | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::CorpWuURL)                                      |
| update_management_WUStatusServer                      | ""      | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::CorpWuURL)                                      |
| update_management_UpdateServiceUrlAlternate           | ""      | [![getadmx doc](https://img.shields.io/badge/getadmx-doc-blue.svg)](https://getadmx.com/?Category=Windows_10_2016&Policy=Microsoft.Policies.WindowsUpdate::CorpWuURL)                                      |

## Dependencies

None

## Example Playbook

```yml
- hosts: all
  roles:
    - sbaerlocher.update-management
```

## Changelog

### 1.0.0

- inital commit

## Author

- [Simon Bärlocher](https://sbaerlocher.ch)

## License

This project is under the MIT License. See the [LICENSE](https://sbaerlo.ch/licence) file for the full license text.

## Copyright

(c) 2020, Arillso
