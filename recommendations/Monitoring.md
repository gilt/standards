# Monitoring

## Adopt

  - [Newrelic](http://newrelic.com/)
    NewRelic is easy to plug into apps, easy to trigger events to a number of platforms (HipChat, PagerDuty, etc), and provides a ton of functionality.

  - [CloudWatch](http://aws.amazon.com/cloudwatch/)

## Assess
  - [Cave](https://github.com/gilt/cave)
  - [Prometheus](https://prometheus.io/)
  - [Grafana](http://grafana.org/)

## Hold

  - [Nagios](https://www.nagios.org)

    A large amount of our development monitoring isn't around hosts and/or NewRelic is doing it better, with less maintenance.
    There are some corner cases where Nagios does a few things better/easier, but unless you have said cases and are ok with managing your own Nagios instance, Nagios probably isn't the tool for you.
