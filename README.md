# Gilt Standards

Standards and guidelines for defining standards at Gilt (Oh My!)

When we talk about standards, we are talking about collaboration with
other teams as well as 3rd parties. From this point of view, our
standards are (deliberately) very basic requirements, mostly
influenced by our combined experiences of working with 3rd
parties. Things that make our lives easier as 'consumers' of 3rd party
APIs are things we now like to do ourselves for our internal APIs as
well. Gilt standards are requirements for work at Gilt.

We also highligt suggestions or recommendations; and they are just
that - you can diverge. We recommend something because we have good
experiences with it, we intend to support it and it gets the job
done. That said, if you think you can do better - that's perfectly
fine, all it means is your team might be on its own and will need to
support the choice.

## List of Standards

* [Open Source](https://github.com/gilt/standards-open-source)
* [REST](https://github.com/gilt/standards-rest)

## Creating a Standard

1. Create a GitHub repository named ```standards-foo``` where ```foo``` is the
   object of the standard. Some examples are: events, schemas, apis, ux, etc.

2. Submit a pull request adding your standard to the [list of
   standards](https://github.com/gilt/standards#list-of-standards) above.


## Governance

We recommend thorough review of changes to standards. The recommended
repository structure at Gilt is:

1. Create a MAINTAINERS file in the root of the repository listing all of the
   people whose opinion we really need in reviewing changes to the standards.
   Each line in the maintainers file should follow the structure:

   ```<github username> (full name)```

   The first line of the file should be the [Benevolent Dictator for
   Life](https://en.wikipedia.org/wiki/Benevolent_dictator_for_life). In the
   maintainers file, append "BDFL" to appropriate name.

   See [the MAINTAINERS file for this
   repo](https://github.com/gilt/standards/blob/master/MAINTAINERS) for an
   example.

2. Create a team in github named "governance-<standard>" with `write` access
   to the repository (all others having `read`-only access).

3. Create a "CONTRIBUTING.md" file in the root of the repository that
   describes the policy by which contributions will be accepted. The standard
   Gilt policy is modeled after the docker hub project. Please feel free to
   link directly to the [standard CONTRIBUTING.md
   policy](https://github.com/gilt/standards/blob/master/CONTRIBUTING.md) for
   your project.


## Contributing

[See Contribution Guidelines](blob/master/CONTRIBUTING.md)

## Frequently Asked Questions

[See FAQ](blob/master/FAQ.md)

