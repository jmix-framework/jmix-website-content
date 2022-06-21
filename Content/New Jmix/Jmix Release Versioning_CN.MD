# Jmix Release Versioning
# Jmix 发布版本说明
## RELEASE VERSIONING
## 发布版本

Jmix release numbers follow a loose form of Semantic Versioning:
Jmix 发布版本号遵循松散的语义版本格式：
Versions are numbered in the form X.Y.Z, where:
版本号使用 X.Y.Z 格式编号，这里：

- X.0.0 is a **major release**, for example 1.0.0, 2.0.0
- X.Y.0 is a **minor release**, for example 1.1.0, 2.3.0
- X.Y.Z is a **patch release**, for example 1.0.1, 1.2.5

- X.0.0 是 **主要版本**，例如 1.0.0，2.0.0
- X.Y.0 是 **次要版本**，例如 1.1.0，2.3.0
- X.Y.Z 是 **补丁版本**，例如 1.0.1，1.2.5


Major and minor releases introduce new features and are called **feature releases**.
主要和次要版本会引入新功能，称为 **功能版本**。

**Patch releases** bring mostly bugfixes and fixes for important performance and security issues. Patch releases are 100% backwards compatible with the previous patch release. The only exception to this rule is when a security issue or data loss bug cannot be fixed without breaking backwards compatibility. If this happens, the release notes provide detailed instructions for upgrade.
**补丁版本** 主要提供错误修复和重要的性能和安全问题的修复。新发布的补丁版本与之前的补丁版本 100% 向后兼容。此规则的唯一例外是，为了修复安全问题或数据丢失错误不得不破坏向后的兼容性。如果发生这种情况，发行说明将提供升级的详细说明。

**Minor feature releases** are mostly backwards compatible with the previous minor release. Exceptions to this rule are listed in the release notes as well as a way to address them. Usually, the required modifications in the source code and application configurations are applied automatically by Jmix Studio during a version upgrade.
**次要功能版本** 大多与之前的次要版本向后兼容。发行说明中会列出此规则的例外情况以及解决这些问题的方法。通常，在版本升级过程中，Jmix Studio 会自动对源代码和应用程序配置做出必要的修改。

**Major feature releases** may introduce incompatible changes in the Jmix architecture, API and functionality. However, Jmix Studio provides an automatic migration procedure to minimize the impact of changes in Jmix to application projects.
**主要功能版本** 可能会在 Jmix 架构、API 和功能中引入不兼容的更改。但是，Jmix Studio 提供了一个自动迁移程序，以最大程度地减少 Jmix 改动对应用项目的影响。

## DEPRECATION POLICY
## 弃用策略
A feature release may deprecate some features from previous releases. Deprecated features will continue to work in all minor releases of the same major version and may be removed in the next major release.
功能版本可能会弃用以前版本中的某些功能。已弃用的功能将继续在同一主要版本的所有次要版本中提供，并可能在下一个主要版本中删除。

For example, if a feature is deprecated in Jmix 1.1, it will continue to work in 1.2, 1.3, 1.x, and will be removed in Jmix 2.0.
例如，如果某个功能在 Jmix 1.1 中被弃用，那么它将在 1.2、1.3、1.x 中继续提供，并在 Jmix 2.0 中删除。

## RELEASE CADENCE
## 发布节奏
Jmix uses a time-based release schedule, with feature releases every 4 months. Major versions are released at least once in 2 years. We recommend upgrading to each latest feature release if your project is in active development.
Jmix 使用基于时间的发布计划，每 4 个月发布一个功能版本。主要版本至少每 2 年发布一次。如果您的项目处于活跃的开发阶段，我们建议您在每个最新功能版本发布时进行升级。

Latest minor releases of each major version are designated as long-term support (LTS) releases. For example: 1.0, 1.1 (LTS), 2.0, 2.1, 2.2 (LTS), 3.0. If your project is at the final stage of development or already shipped to production, you can stay on the latest LTS release to receive only critical updates.
每个主要版本的最新次要版本为长期支持（LTS）版本。例如：1.0、1.1（LTS）、2.0、2.1、2.2（LTS）、3.0。如果您的项目处于开发的最后阶段或已经部署至生产环境，则可以停留在最新的 LTS 版本，仅进行关键更新。

## VERSION SUPPORT POLICY
## 版本支持策略
At any given time, we support a set of feature releases to varying degrees.
任何时候，我们都会不同程度的为一组功能版本提供支持。

The last feature release is in **active support**: it receives fixes for security issues, critical bugs, major functionality issues in new features of this release, regressions from older releases introduced in the current release.
**主动支持** 最新的功能版本：接收有关安全问题，关键错误，此版本新功能中的主要功能问题的修复，以及当前版本中引入的旧版本的回归问题修复。

Active support of non-LTS releases lasts 4 months until the next minor or major version is released. LTS releases are in active support for 8 months.
对非 LTS 版本的主动支持持续 4 个月，直到下一个次要或主要版本发布。LTS 版本提供 8 个月的主动支持。

After the active support phase, a feature release moves to the maintenance phase. Maintenance means fixing critical security vulnerabilities and data loss bugs. Fixes are provided in a new patch release of the supported version.
在主动支持阶段之后，功能版本将进入维护阶段。维护表示仅修复关键的安全漏洞和数据丢失错误。修复内容仅在还处于维护期内版本的补丁版本中提供。

**Free maintenance** is provided for 3 years for each LTS release and for 4 months for each non-LTS release.
为每一个 LTS 版本提供 3 年的 **免费维护**，为每一个非 LTS 版本提供 4 个月的免费维护。

**Commercial maintenance** is available for any feature release of Jmix, issued within 10 past years. This option could be useful for projects with a long lifecycle. You can learn more about the commercial maintenance service here.
**商业维护** 适用于过去 10 年内发布的 Jmix 的任何功能版本。如果项目有很长的维护周期，可以选择此方案。有关商业维护服务的更多信息，请访问 [这里](https://www.haulmont.com/services/cuba-platform-services/support/)

If a critical security vulnerability or a data loss bug is caused by an external third-party dependency, we update the dependency if there is a newer fixed version. There may be cases when we may be unable to include the newer version of a dependency if architectural changes for that version prevent its usage in Jmix or the effort required to integrate the new version exceeds reasonable commercial efforts.
如果严重安全漏洞或数据丢失错误是由第三方外部依赖引起的，如果对方提供更新修复版本，我们会更新依赖。在某些情况下，如果某个依赖的架构变化导致该依赖在 Jmix 中无法使用，或者集成新版本所需的工作超出了合理的商业成本，则我们可能无法提供针对该新版本的修复。

