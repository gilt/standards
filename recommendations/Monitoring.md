# Monitoring

## Adopt

  - [Newrelic](http://newrelic.com/)
    NewRelic is easy to plug into apps, easy to trigger events to a number of platforms (HipChat, PagerDuty, etc), and provides a ton of functionality.

  - [CloudWatch](http://aws.amazon.com/cloudwatch/)

## Assess
  - [Cave](https://github.com/gilt/cave)
  - [Prometheus](https://prometheus.io/) is an open-source systems monitoring and alerting toolkit originally built at SoundCloud. It is easy to configure and maintain. It has clients for most prominent languages (java, node, scala). It consists of multiple modules, two of which are Prometheus Alerts that provides great Alerting capabilites and the Node Exporter, that allows to export *plenty* of OS metrics
  - [Grafana](http://grafana.org/) provides a powerful and elegant way to create, explore, and share dashboards and data with your team and the world. It is currently the most popular *grapher* used to display Prometheus data.

## Hold

  - [Nagios](https://www.nagios.org)

    A large amount of our development monitoring isn't around hosts and/or NewRelic is doing it better, with less maintenance.
    There are some corner cases where Nagios does a few things better/easier, but unless you have said cases and are ok with managing your own Nagios instance, Nagios probably isn't the tool for you.
