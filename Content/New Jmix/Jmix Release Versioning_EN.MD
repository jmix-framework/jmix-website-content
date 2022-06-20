# Jmix Release Versioning
## RELEASE VERSIONING

Jmix release numbers follow a loose form of Semantic Versioning:
Versions are numbered in the form X.Y.Z, where:

- X.0.0 is a **major release**, for example 1.0.0, 2.0.0
- X.Y.0 is a **minor release**, for example 1.1.0, 2.3.0- ЧюНю0 шы ф **ьштщк кудуфыу**б ащк учфьзду 1ю1ю0б 2ю3ю0

- X.Y.Z is a **patch release**, for example 1.0.1, 1.2.5


Major and minor releases introduce new features and are called **feature releases**.

**Patch releases** bring mostly bugfixes and fixes for important performance and security issues. Patch releases are 100% backwards compatible with the previous patch release. The only exception to this rule is when a security issue or data loss bug cannot be fixed without breaking backwards compatibility. If this happens, the release notes provide detailed instructions for upgrade.

**Minor feature releases** are mostly backwards compatible with the previous minor release. Exceptions to this rule are listed in the release notes as well as a way to address them. Usually, the required modifications in the source code and application configurations are applied automatically by Jmix Studio during a version upgrade.

**Major feature releases** may introduce incompatible changes in the Jmix architecture, API and functionality. However, Jmix Studio provides an automatic migration procedure to minimize the impact of changes in Jmix to application projects.

## DEPRECATION POLICY
A feature release may deprecate some features from previous releases. Deprecated features will continue to work in all minor releases of the same major version and may be removed in the next major release.

For example, if a feature is deprecated in Jmix 1.1, it will continue to work in 1.2, 1.3, 1.x, and will be removed in Jmix 2.0.

## RELEASE CADENCE
Jmix uses a time-based release schedule, with feature releases every 4 months. Major versions are released at least once in 2 years. We recommend upgrading to each latest feature release if your project is in active development.

Latest minor releases of each major version are designated as long-term support (LTS) releases. For example: 1.0, 1.1 (LTS), 2.0, 2.1, 2.2 (LTS), 3.0. If your project is at the final stage of development or already shipped to production, you can stay on the latest LTS release to receive only critical updates.

## VERSION SUPPORT POLICY
At any given time, we support a set of feature releases to varying degrees.

The last feature release is in **active support**: it receives fixes for security issues, critical bugs, major functionality issues in new features of this release, regressions from older releases introduced in the current release.

Active support of non-LTS releases lasts 4 months until the next minor or major version is released. LTS releases are in active support for 8 months.

After the active support phase, a feature release moves to the maintenance phase. Maintenance means fixing critical security vulnerabilities and data loss bugs. Fixes are provided in a new patch release of the supported version.

**Free maintenance** is provided for 3 years for each LTS release and for 4 months for each non-LTS release.

**Commercial maintenance** is available for any feature release of Jmix, issued within 10 past years. This option could be useful for projects with a long lifecycle. You can learn more about the commercial maintenance service here.

If a critical security vulnerability or a data loss bug is caused by an external third-party dependency, we update the dependency if there is a newer fixed version. There may be cases when we may be unable to include the newer version of a dependency if architectural changes for that version prevent its usage in Jmix or the effort required to integrate the new version exceeds reasonable commercial efforts.