# Load Testing

## Adopt

#### Core Service Focused Performance Tests

We think that in an Amazon Cloud scenario (where services can scale up
and down subject to an appropriate load metric) a meaningful
performance test should only try to measure how much load a *single*
instance of a service can comfortably take enabling its owners to 'do
the math' and plan a reasonable auto scaling policy for known events
(e.g. Noon).

E.g. Assuming we have an elastic enabled svc-foo we could write a
small, focused performance test able to inject load on a single
instance of this svc telling us how much could take in the limit of
acceptable SLAs (e.g. 95th percentile). Having this info and a rough
estimate of the max load it could take in Production we then are in a
position where we can confidently write an auto scaling policy with an
high percentage of success.

This kind of test could be easily automated by writing a simple CI job
that always tests a canary node in Production making possible to spot
performance regressions without stressing the entire cluster.

Making this test an integral part of the service (as a sub-project in
the same Git repo would be ideal) will also promote ownership.

Our recent move to AWS facilitates the automation of this kind of
tests. Most of our deployments already have the concept of a 'canary'
node that is used to 'test in production' a new release before rolling
out to the entire cluster. We propose to use this node as a target for
a possibly automated load test. Better would be to have also a 'dark
canary' that is isolated by production traffic in order to have a
completely unaffected test. However, with a correct timing, we could
use a best effort approach and run the load test when the traffic is
very low having always roughly the same baseline of 'noise'. Amazon
APIs are really helpful for auto-discovering 'target' nodes for the
test; a super simple approach would be to tag the dark/canary node and
use this tag from an aws ec2 'describe' operation to look up for the
ip address of the node (see this
[gist](https://gist.github.com/umatrangolo/cf17f4f463cdd9efd33894fc60eb29de)
as an example).

#### Gatling

Writing an effective performance test able to verify that the most
critical paths of your service are well prepared to handle a given
load is not that difficult when using the right tools.

One performance test framework we have based our load testing upon
since the beginning is [Gatling](http://gatling.io/). We like its
expressive Scala based DSL to layout simulations and its ease of
use. It also offers a comprehensive reporting to quickly pinpoint
performance regressions.

A significant
[example](https://gist.github.com/umatrangolo/3cd6a16c322ece72a58831a10ea9bbfa)
of a core service that is tested with the help of this tool is
svc-user. The simulation code is very small but it is able to test the
top four most used endpoints in the service. We offer a gist of it
showing that what it takes to write a meaningful test with Gatling is
no more than 100 lines of code. After building a fat jar out of it, it
is then possible to run on the spot a test for quickly validating a
new version (you could even run it from your laptop) or automate it in
a proper CI pipeline (e.g. last step after deploying a canary).

## Trial

## Assess

## Hold

#### Site Wide Performance Tests

The current performance testing framework is based on a series of
custom built, Gatling based, fat jars deployed on EC2 injector
machines hitting a given cluster to test its resilience against a
pre-configured load. The various tests are orchestrated by a set of
Jenkins jobs kicking off at a predetermined time, each day.

E.g. the '''perf_test_daily_long''' job on production Jenkins has been
used for a while to test the entire Gilt site end to end. This test
was trying to simulate many concurrent users browsing the site jumping
back and forth between account pages, sale listings and product
details.

The above scenario was reasonable when we were hosting all our
infrastructure on proprietary hardware hosted in Carpathia but it is
now proving to be challenging and inadequate after our move to the
Amazon Cloud.

The main problem with our current performance tests is that they are
not worth much in a scenario where we use auto scaling groups to react
to increased load. The net result is a daily test that proves nothing
and produces a series of small outages due to legacy services still
not able to scale up/down as required.

An often proposed argument against HOLDing on this kind of tests is
that we actually need to know if we can scale in face of an unexpected
given load; we can already give an answer to this question: we
can't. Given the peculiar shape of the load that the GILT site faces
every day (much like a big spike around Noon) we can surely say that
any auto scaling policy purely based only on load/cpu utilization
won't be fast enough to cope with a very steep load ramp. This is a
known problem and there already is a proposal for a notification
system that could be used to schedule asg events for unknown sales
outside the usual time windows.
