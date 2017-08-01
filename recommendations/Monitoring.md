# Monitoring

## Adopt

  - [Newrelic](http://newrelic.com/)
    NewRelic is easy to plug into apps, easy to trigger events to a number of platforms (HipChat, PagerDuty, etc), and provides a ton of functionality.

  - [CloudWatch](http://aws.amazon.com/cloudwatch/)

## Assess
  - [Prometheus](https://prometheus.io/) is an open-source systems
    monitoring and alerting toolkit originally built at SoundCloud. It
    is easy to configure and maintain. It has clients for most
    prominent languages (java, node, scala). It consists of multiple
    modules, two of which are Prometheus Alerts that provides great
    Alerting capabilites and the Node Exporter, that allows to export
    *plenty* of OS metrics
  - [Grafana](http://grafana.org/) provides a powerful and elegant way
    to create, explore, and share dashboards and data with your team
    and the world. It is currently the most popular *grapher* used to
    display Prometheus data.

## Hold

  - [Nagios](https://www.nagios.org)
    A large amount of our development monitoring isn't around hosts
    and/or NewRelic is doing it better, with less maintenance.  There
    are some corner cases where Nagios does a few things
    better/easier, but unless you have said cases and are ok with
    managing your own Nagios instance, Nagios probably isn't the tool
    for you.

  - [Cave](https://github.com/gilt/cave)
    Started with all good intentions this project now is unmaintained
    and the chance to evolve it are close to zero. There is a lot of
    back-end work needed to move it to a more recent version of its
    tech stack (e.g. InfluxDb) that is not going to be addressed any
    time soon. The net result is that a critical part of our
    monitoring/alerting infrastructure is delegated to something that
    has been let to rot for years with no plan for the future. We will
    be much better served by a more pervasive use of CloudWatch alerts
    that could cover 90% of the current use cases.
