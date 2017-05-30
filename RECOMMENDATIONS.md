# Technology recommendations at Gilt

This is our shared assessment of the various technologies
currently used at Gilt or potentially useful to Gilt.

See [README](README.md) for a general discussion about the
differences between RECOMMENDATIONS and STANDARDS.

Techologies listed here are tagged with one of **Adopt**, **Trial**, **Assess**, **Hold**, in the spirit of
[Thoughtworks technology radar](http://www.thoughtworks.com/radar/faq)


- **Adopt**: We feel strongly that the we should be using these
  technologies. Use them when appropriate on your projects.

- **Trial**: Worth pursuing. It is important to understand how to
  build up this capability. There is still a lot of risk as the
  technology is not yet fully supported by teams at Gilt.

- **Assess**: Worth exploring with the goal of understanding how it will
  fit at Gilt - does it solve a new problem or improve an existing one?

- **Hold**: Proceed with caution before introducing new reliance on the technology. Something may be on hold for a variety of reasons:
	- The technology is being explicitly deprecated
	- The vendor of the technology has issued a replacement (eg., Objective-C vs. Swift)
	- Previous use of the technology at Gilt has failed in some way

Depending on your personal attitude and the needs of your project you can either stick to
a stack of *adopt*ed technologies or experiment. Probably a good idea to reduce our
footprint of on *hold* technologies over time.

If you feel that something is not listed here but should be - submit a pull request.


# List of recommendations

- [Databases](recommendations/Databases.md)
- [Deployment](recommendations/Deployment.md)
- [Jobs](recommendations/Jobs.md)
- [Messaging](recommendations/Messaging.md)
- [Monitoring](recommendations/Monitoring.md)
- [Operating Platforms](recommendations/OperatingPlatforms.md)
- [Programming Languages](recommendations/ProgrammingLanguages.md)
- Frameworks
  - [Scala Frameworks](recommendations/frameworks/Scala.md)
  - [JavaScript Frameworks](recommendations/frameworks/JavaScript.md)
  - [GraphQL](recommendations/frameworks/GraphQL.md)
- [QA](recommendations/Quality.md)
- [Testing In Production](recommendations/Quality-TIP.md)
- [Source Code Management](recommendations/SourceCodeManagement.md)
- [Continuous Integration](recommendations/ContinuousIntegration.md)
- [Performance Testing](recommendations/PerformanceTesting.md)
