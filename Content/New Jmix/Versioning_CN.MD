# Stable Release Versioning
# 稳定发布版本说明

CUBA follows a standard semantic numeration for its stable versions - major.minor.maintenance, e.g.
CUBA 的稳定发布版本遵循标准语义计数 - major.minor.maintenance，即
- Major version
  主要版本（Major）
- Minor version
  次要版本（Minor）
- Maintenance version
  维护版本（Maintenance）
## MAINTENANCE RELEASE
## 维护版本
A maintenance release is backwards compatible, bringing mostly bugfixes, minor improvements, fixes for critical performance and security issues. In rare cases, it may include some minor features or API enhancements, which do not introduce breaking changes.
维护版本支持向后兼容，主要包含错误修复，小改进，关键性能和安全问题的修复。在极少数情况下，也可能包括一些小功能或 API 增强，这些功能或增强不会引入破坏性改动。

## MINOR RELEASE
## 次要版本
A minor release is mostly backwards compatible, however, it may include some breaking changes on the functional and API levels. All breaking changes are listed in the release notes as well as a way to address them. Often, the required modifications in the source code and application configurations are applied automatically by CUBA after a version upgrade. A minor release is intended to introduce new features, meanwhile keeping upgrade procedure fast and easy.
次要版本大多支持向后兼容，但是，可能包含功能和 API 级别的一些破坏性改动。发行说明中会列出所有破坏性改动及其解决方案。通常，在版本升级后，CUBA 会自动对源码和应用程序配置做必要的改动。次要版本的目的在于引入新功能，同时保持升级过程快速简便。

## MAJOR UPDATE
## 主要版本
A major update is intended to introduce the latest popular development paradigms, approaches and massive improvements in architecture and functionality. Generally, it introduces incompatible changes in the core architecture, functional features, application-level API, underlying libraries and their versions. Major updates have no obligation to be backwards compatible; nevertheless, in new major versions, legacy API is not removed but goes deprecated, meaning that formal upgrade may be performed relatively easy.
主要版本更新的目的在于引入最新的流行开发范例、方法以及架构和功能方面的大规模改进。通常，主要版本会在核心架构、功能特性、应用程序级 API、底层库及其版本中引入不兼容的改动。主要版本没有向后兼容的义务，但是，在新的主要版本中，不会删除旧版 API，而仅仅是弃用，让升级过程相对容易。

## Support Terms
## 支持条款
### Free maintenance - 5 YEARS
### 5 年免费维护
is provided for 5 years for each latest minor version. This means maintenance releases will be issued within 5 years since the latest stable minor update is released for each major version of CUBA. Free maintenance is also provided for 3 months for the previous minor version of each major release since the new minor version gets released. Such a period is assumed to be enough to update your application to the latest minor version.
我们为每个最新的次要版本提供 5 年免费维护期。也就是说，CUBA 的每个主要版本的最后一个次要版本发布后，会在 5 年内提供针对该次要版本的维护版本。在每个主要版本的最新次要版本发布后，也针对前一个次要版本提供 3 个月的免费维护，这段时间足以将应用程序更新到最新的次要版本。

Please note, that while we are committed to sticking to this free maintenance policy, it is not a legally binding offer and may possibly change.
请注意，虽然我们会尽力遵守此免费维护政策，但这不是具有法律约束力的要约，可能会更改。

## Commercial maintenance - 10 YEARS
## 10 年商业维护
is available for any minor version of CUBA, issued within 10 past years. This option could be useful for projects with a long update cycle. Also, staying on the latest minor version longer than 5 years, it is also possible to use this option to extend maintenance for another 5 years.
我们为过去 10 年中发布的任何 CUBA 主要版本提供商业维护。如果项目有很长的维护周期，可以选择此方案。另外，如果使用最新的次要版本超过 5 年的免费维护期，也可以选择此方案延长 5 年维护期。

You can learn more about the commercial maintenance service [here](https://www.jmix.io/services-support/).
更多关于商业维护服务的内容，请访问 [这里](https://www.jmix.io/services-support/)。

## End of life - AFTER
## 停止维护
of a version happens after 10 years (3650 days) since the release date. In other words, versions older than 10 years are not maintained even on a commercial basis.
自版本发布之日起 10 年后将不再提供维护。即，超过 10 年的版本不提供免费或商业维护。

Maintenance means fixing critical security vulnerabilities and data loss bugs. Fixes are provided in a new patch release of the supported version.
维护内容为修复关键的安全漏洞和数据丢失错误。修复内容仅在还处于维护期内版本的维护版本中提供。

If a critical security vulnerability or a data loss bug is caused by a third-party external dependency, we update the dependency if there is a newer fixed version. There may be cases when we may be unable to include the newer version of a dependency if architectural changes for that version prevent its usage in CUBA or the effort required to integrate the new version exceeds reasonable commercial efforts.
如果严重安全漏洞或数据丢失错误是由第三方外部依赖引起的，如果对方提供更新修复版本，我们会更新依赖。在某些情况下，如果某个依赖的架构变化导致该依赖在 CUBA 中无法使用，或者集成新版本所需的工作超出了合理的商业成本，则我们可能无法提供针对该新版本的修复。

- VERSION	
- RELEASE DATE	
- MAINTENANCE STATUS	
- COMMERCIAL MAINTENANCE ON	
- EOL ON
6.1	Mar 30, 2016	Commercial	-	Mar 30, 2026
6.2	Jun 07, 2016	Commercial	-	Jun 07, 2026
6.3	Oct 19, 2016	Commercial	-	Oct 19, 2026
6.4	Jan 31, 2017	Commercial	-	Jan 31, 2027
6.5	Apr 21, 2017	Commercial	-	Apr 21, 2027
6.6	Jul 28, 2017	Commercial	-	Jul 28, 2027
6.7	Oct 31, 2017	Commercial	-	Oct 31, 2027
6.8	Jan 31, 2018	Commercial	-	Jan 31, 2028
6.9	May 30, 2018	Commercial	-	May 30, 2028
6.10	Sep 27, 2018	免费	Sep 27, 2023	Sep 27, 2028
7.0	Jan 24, 2019	Commercial	-	Jan 24, 2029
7.1	Sep 05, 2019	Commercial	-	Sep 05, 2029
7.2	March 01, 2020	免费	March 01, 2025	March 01, 2030

- VERSION	
  版本
- RELEASE DATE	
  发布日期
- MAINTENANCE STATUS	
  维护状态
- COMMERCIAL MAINTENANCE ON	
  仅提供商业维护
- EOL ON
  维护截止
6.1	2016-03-30	商业维护	-	2026-03-30
6.2	2016-06-07	商业维护	-	2026-06-07
6.3	2016-10-19	商业维护	-	2026-10-19
6.4	2017-01-31	商业维护	-	2027-01-31
6.5	2017-04-21	商业维护	-	2027-04-21
6.6	2017-07-28	商业维护	-	2027-07-28
6.7	2017-10-31	商业维护	-	2027-10-31
6.8	2018-01-31	商业维护	-	2028-01-31
6.9	2018-05-30	商业维护	-	2028-05-30
6.10	2018-09-27	免费	2023-09-27	2028-09-27
7.0	2019-01-24	商业维护	-	2029-01-24
7.1	2019-09-05	商业维护	-	2029-09-05
7.2	2020-03-01	免费	2025-03-01	2030-03-01
