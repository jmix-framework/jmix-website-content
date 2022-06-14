# Stable Release Versioning
CUBA follows a standard semantic numeration for its stable versions - major.minor.maintenance, e.g.
- Major version
- Maintenance version
- Minor version

## MAINTENANCE RELEASE
A maintenance release is backwards compatible, bringing mostly bugfixes, minor improvements, fixes for critical performance and security issues. In rare cases, it may include some minor features or API enhancements, which do not introduce breaking changes.

## MINOR RELEASE
A minor release is mostly backwards compatible, however, it may include some breaking changes on the functional and API levels. All breaking changes are listed in the release notes as well as a way to address them. Often, the required modifications in the source code and application configurations are applied automatically by CUBA after a version upgrade. A minor release is intended to introduce new features, meanwhile keeping upgrade procedure fast and easy.

## MAJOR UPDATE
A major update is intended to introduce the latest popular development paradigms, approaches and massive improvements in architecture and functionality. Generally, it introduces incompatible changes in the core architecture, functional features, application-level API, underlying libraries and their versions. Major updates have no obligation to be backwards compatible; nevertheless, in new major versions, legacy API is not removed but goes deprecated, meaning that formal upgrade may be performed relatively easy.

## Support Terms
### Free maintenance - 5 YEARS
is provided for 5 years for each latest minor version. This means maintenance releases will be issued within 5 years since the latest stable minor update is released for each major version of CUBA. Free maintenance is also provided for 3 months for the previous minor version of each major release since the new minor version gets released. Such a period is assumed to be enough to update your application to the latest minor version.

Please note, that while we are committed to sticking to this free maintenance policy, it is not a legally binding offer and may possibly change.

## Commercial maintenance - 10 YEARS
is available for any minor version of CUBA, issued within 10 past years. This option could be useful for projects with a long update cycle. Also, staying on the latest minor version longer than 5 years, it is also possible to use this option to extend maintenance for another 5 years.

You can learn more about the commercial maintenance service [here](https://www.jmix.io/services-support/).

## End of life - AFTER
of a version happens after 10 years (3650 days) since the release date. In other words, versions older than 10 years are not maintained even on a commercial basis.

Maintenance means fixing critical security vulnerabilities and data loss bugs. Fixes are provided in a new patch release of the supported version.

If a critical security vulnerability or a data loss bug is caused by a third-party external dependency, we update the dependency if there is a newer fixed version. There may be cases when we may be unable to include the newer version of a dependency if architectural changes for that version prevent its usage in CUBA or the effort required to integrate the new version exceeds reasonable commercial efforts.

- VERSION	RELEASE 
- DATE	
- MAINTENANCE STATUS	
- COMMERCIAL MAINTENANCE 
- ON	EOL ON
6.1	Mar 30, 2016	Commercial	-	Mar 30, 2026
6.2	Jun 07, 2016	Commercial	-	Jun 07, 2026
6.3	Oct 19, 2016	Commercial	-	Oct 19, 2026
6.4	Jan 31, 2017	Commercial	-	Jan 31, 2027
6.5	Apr 21, 2017	Commercial	-	Apr 21, 2027
6.6	Jul 28, 2017	Commercial	-	Jul 28, 2027
6.7	Oct 31, 2017	Commercial	-	Oct 31, 2027
6.8	Jan 31, 2018	Commercial	-	Jan 31, 2028
6.9	May 30, 2018	Commercial	-	May 30, 2028
6.10	Sep 27, 2018	Free	Sep 27, 2023	Sep 27, 2028
7.0	Jan 24, 2019	Commercial	-	Jan 24, 2029
7.1	Sep 05, 2019	Commercial	-	Sep 05, 2029
7.2	March 01, 2020	Free	March 01, 2025	March 01, 2030


