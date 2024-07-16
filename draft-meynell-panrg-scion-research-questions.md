---
title: "SCION Research Questions"
abbrev: "scion-research_I-D"
category: info
submissiontype: IRTF

docname: draft-meynell-panrg-scion-research-questions-latest

v: 3
area: IRTF
workgroup: PANRG
keyword: Internet-Draft
venue:
  group: WG
  type: Working Group
  mail: panrg@irtf.org
  arch: https://datatracker.ietf.org/rg/panrg
  github: "scionassociation/scion-research_I-D"
  latest: "https://scionassociation.github.io/scion-research_I-D/draft-meynell-panrg-scion-research-questions.html"

author:
 -   ins: K. Meynell
     name: Kevin Meynell
     org: SCION Association
     email: kme@scion.org

 -   ins: J. García Pardo
     name: Juan A. García Pardo Giménez de los Galanes
     org: ETH Zürich
     email: juan.garcia@inf.ethz.ch

 -   ins: T. Zäschke
     name: Tilmann Zäschke
     org: ETH Zürich
     email: tilmann.zaeschke@inf.ethz.ch

 -   ins: N. Rustignoli
     name: Nicola Rustignoli
     org: SCION Association
     email: nic@scion.org

normative:
  RFC9217:
  I-D.ietf-quic-multipath:
  I-D.scion-cp:
    title: SCION Control Plane
    date: 2023
    target: https://datatracker.ietf.org/doc/draft-dekater-scion-controlplane/
    author:
      -
        ins: C. de Kater
        name: Corine de Kater
        org: SCION Association
      -
        ins: N. Rustignoli
        name: Nicola Rustignoli
        org: SCION Association
      -
        ins: S. Hitz
        name: Samuel Hitz
        org: Anapaya Systems
  I-D.scion-cppki:
    title: SCION Control-Plane PKI
    date: 2023
    target: https://datatracker.ietf.org/doc/draft-dekater-scion-pki/
    author:
      -
        ins: C. de Kater
        name: Corine de Kater
        org: SCION Association
      -
        ins: N. Rustignoli
        name: Nicola Rustignoli
        org: SCION Association
      -
        ins: S. Hitz
        name: Samuel Hitz
        org: Anapaya Systems
  I-D.scion-dataplane:
    title: SCION Data Plane
    date: 2023
    target: https://datatracker.ietf.org/doc/draft-dekater-scion-dataplane/
    author:
      -
        ins: C. de Kater
        name: Corine de Kater
        org: SCION Association
      -
        ins: N. Rustignoli
        name: Nicola Rustignoli
        org: SCION Association
      -
        ins: S. Hitz
        name: Samuel Hitz
        org: Anapaya Systems
informative:
  I-D.garciapardo-drkey:
    title: Dynamically Recreatable Keys
    date: 2022
    target: https://datatracker.ietf.org/doc/draft-garciapardo-panrg-drkey/
    author:
      -
        ins: J. Pardo
        name: Juan A. García Pardo Giménez de los Galanes
        org: ETH Zürich
      -
        ins: C. Krähenbühl
        name: Cyrill Krähenbühl
        org: ETH Zürich
      -
        ins: B. Rothenberger
        name: Benjamin Rothenberger
        org: ETH Zürich
      -
        ins: A. Perrig
        name: Adrian Perrig
        org: ETH Zürich
  LEGNER2020:
    title: "EPIC: Every Packet Is Checked in the Data Plane of a Path-Aware Internet"
    date: 2020
    target: https://netsec.ethz.ch/publications/papers/Legner_Usenix2020_EPIC.pdf
    author:
      -
        ins: M. Legner
        name: Markus Legner
        org: ETH Zürich
      -
        ins: T. Klenze
        name: Tobias Klenze
        org: ETH Zürich
      -
        ins: M. Wyss
        name: Marc Wyss
        org: ETH Zürich
      -
        ins: C. Sprenger
        name: Christoph Sprenger
        org: ETH Zürich
      -
        ins: A. Perrig
        name: Adrian Perrig
        org: ETH Zürich

  KRAHENBUHL2023:
    title: "FABRID: Flexible Attestation-Based Routing for Inter-Domain Networks"
    date: 2020
    target: https://www.usenix.org/conference/usenixsecurity23/presentation/krahenbuhl
    author:
      -
        ins: C. Krähenbühl
        name: Cyrill Krähenbühl
        org: ETH Zürich
      -
        ins: M. Wyss
        name: Marc Wyss
        org: ETH Zürich
      -
        ins: D. Basin
        name: David Basin
        org: ETH Zürich
      -
        ins:  V. Lenders
        name:  Vincent Lenders
        org: Armasuisse
      -
        ins: A. Perrig
        name: Adrian Perrig
        org: ETH Zürich
      -
        ins:  M. Strohmeier
        name:  Martin Strohmeier
        org: Armasuisse
--- abstract

TODO Abstract here


--- middle

# Introduction

SCION is an inter-domain network architecture. Its core components specification, as deployed by some of its early adopters, is outlined in {{I-D.scion-dataplane}}, {{I-D.scion-cppki}}, {{I-D.scion-cp}}, currently under ISE review.

The goal of this draft is to explore how SCION and its early deployments try to address open research questions in {{RFC9217}}. Specifically, there are still many open areas of research around path-aware networking, where SCION with its early deployment experiences and research efforts can provide a contribution. This can also be a starting point for discussions around long-term protocol evolution.

This draft assumes the reader is familiar with some of the fundamental concepts defined in the components specification.

**Note:** This is the very first version of the SCION research questions draft, and it merely contains a skeleton of potential topics to be further discussed in this draft. Any feedback is welcome and much appreciated. Thanks!


# Conventions and Definitions

{::boilerplate bcp14-tagged}

# Discovery, Distribution, and Trustworthiness of Path Properties

## ISD, AS identity

* How many ASes do we expect in the SCION network model?
* How many ISDs? What is the ontology of an ISD? Per geographic area only?
* One AS belongs to many ISDs?


## Beacon Forwarding Policy

The idea behind "beaconing" is to discover all possible paths (loop free and with a fixed maximum length) between two CORE AS.
Every CORE AS forwards any received beacons to all neighbor CORE ASes unless this would cause a loop or exceed the fixed maximum length.
Implemented naively, the number of paths (and beacons) grows exponentially with the network size.
This is currently mitigated, primarily (and efficiently), by forwarding only the five "best PCBs" (from a given remote source CORE AS) to neighbors.
"Best" here takes into account properties such as diversity, time to expire and whether (or how recently) the same
PCBs has been forwarded before.

Since path may expire after an hour or so and because expiration is not the only factor, an AS will typically start
resending the same beacons in less than an hour (i.e. the typical expiration time).

This means the total number of different PCBs that an AS will receive from a given neighbor is e.g.
5 per minute * 30 minute = 150 paths.

Most likely, an AS will receive PCBs originated from a given source from several neighbors, however these are likely to be
very similar. They are likely to have the same tail and only differ in the few last added hops, i.e. the immediate neighbors.

As a result, an AS will probably have only little more than 150 paths to a given remote AS.

This is likely sufficient for most applications, but is far from a complete view of the network.

This can be problematic:

* Massive multipathing: endpoints may not be able to use the theoretically best paths.
* Unusual path policies, such as geofencing, may not be fulfillable by the limited number of paths on offer.


## Wormhole attack

### Set up

Scenario: attackers create two core ASes that are geographically far apart. They then anounce a link (effectively a shortcut) between these two AS with
very appealing properties (low latency, few hops, ...).

### Impact
The attacker can now perform blackhole attacks (DoS), greyhole attacks, delay traffic, or similarily impact traffic.

Critically, there is currently no clear way to recover from this situation. In order to recover, ASes that are connected to the
workhole-ASes would need to learn of the problem and stop forwarding the wormhole beacons.

Mitigations:

- Introduce a way for ASes to verify path properties. This would make it harder to install wormholes.
  This could include measuring latency or sense-checking of geolocation information.
- Introduce a way for endpoints to discover path problems.
- Introduce a way for endpoints to report path problems.
- Introduce a way to recover from malicious segments, see {{signalling-faulty-segments}}.
- Adapt the path discovery and dissemination algorithm to allow ASes to have many more than five paths to
  a given remote destination. The attack would then require an (unreasonably) large number of compromised ASes.

A related question is discussed in {{signalling-faulty-segments}}.



## Segment Dissemination

Control servers may return a large number of path segments for some queries.
This can cost considerable bandwidth / network egress while at the same time
overloading clients with an unnecessarily large numbers of segments.

* This problem may be more acute in ASes with many end hosts (e.g. IoT),
or end hosts with little computing power or little spare bandwidth.
* Getting a full path to a remote endhost may require three round-trips with the control server.

There are multiple possible and independent solution steps here:

* Compression: Segments could be stored in a way that duplicate information (hops & links) is only stored once and the segments contain only references to the hops and links.
* Instead of requiring three separate queries for (UP/CORE/DOWN), we could allow a single query from \<start AS\> to \<end AS\> across multiple segments.
  This should be very easy to implement and would be compatible with the current wire protocol (protobuf).
  * This would reduce the number of round trips to one.
  * It would reduce the number of returned segments because only segments that actually connect to other segments would need to be returned.
* Predefine some policies that can be resolved by the control server, e.g. ANY, BEST_LATENCY, BEST_BANDWIDTH, BEST_PRICE,
BEST_CO2. For these, a control server could simply calculate 5-10 good paths and return these.
Moreover these could be cached for commonly requested remote ASes.
If a user requires a custom policy they can still resort to requesting actual segments.

Doing path selection on the control server will initially increase computational cost.
However, it would substantially decrease network egress. Caching of paths should reduce CPU cost,
maybe even below the current cost for retrieving a large amount of segments from the local database and sending them over the network interface.

Examples for requesting CORE segments between different ISDs or within an ISD (as of 2024-07-12):

| src         | dst         | segments returned |
| ----------: + ----------: + :---------------: |
| 64-0:0:0    | 64-0:0:0    | 337               |
| 64-0:0:0    | 65-0:0:0    | 240               |
| 64-0:0:0    | 67-0:0:0    | 60                |
| 64-0:0:0    | 64-2:0:13   | 60                |
{: #segment-count-example title="CORE segment count examples"}

## Periodic beacon propagation
* Is it necessary to propagate beacons periodically? If so, why? 
  * For path freshness, only the origin needs to originate beacons periodically, and others disseminate immediately.
  * For response to link failures or availability of new paths, beacon services can respond instantly.
* Re-propgating the same set of beacons at each interval is a waste of resources The periodic propagation can be used for the discovery of new paths at each interval, enhancing the scalability, and path diversity.

## Beacon optimization and beaconing extensibility
* Communication quality requirements vary based on source, destination, and applications.
* Satisfying all these criteria either requires discovering all paths in the network, or optimizing paths during the beaconing process.
  * Clearly, the 5-shortest path per destination cannot satisfy all communication requirements.
* What optimization functions should be applied to beacons when propagating them?
  * What are the optimality metrics considered in these functions?
* Who should select these functions?
* How should the deployment of these functions be enforced?
* How can multiple functions be applied concurrently for different src/dst/applications?
* How should end ASes express their desired requirements to the inter-domain control plane?
* How do these requirements translate into concrete optimization functions?
* How does standardization of the functions work? 
* Criteria change over time.
  * How can optimization functions adapt to incorporate these changes?
  * How to achieve fast adaptation of optimization functions?


## Routing Policies and Traffic Engineering

Reduced adoption due to limited routing policy possibilities, such as a (core-)AS does not want to accept transit traffic unless it starts/ends in ASs with special properties. For example a GEANT AS does not want to allow transit traffic unless it originates or ends in another research AS.

One solution could be to add a “confirm full path”-flag to certain segments. If this flag is set, the full path (all segments) needs to authorized by all ASes that insist on authorizing it. This is obviously less scalable but may be viable for ASes that insist on such policies. This also allows for “secret” policies.

Collateral: this probably needs a data plane change. Conceptually, we have only a single resulting segment, and that segment needs to be used in full, e.g. no on-path trickery.

## DRKey
DRKey is a key distribution system that scales well with the number of endpoints in the network.
It relies on two things:

* Two sides of a key: A fast side, and a slow side. Sometimes called fast and slow side of the derivation.
  The ability of deriving a key very quickly on the fast side is necessary for most of its use cases.
* A grouping of endpoints (such as ASes): The pieces necessary to derive a key, namely the L1 keys,
  are communicated to each keystore at each grouping (e.g., a keystore per AS).

The questions related to DRKey are the following ones (not comprehensive):

* Do we want to have any possible authorization that is at the moment carried out at the data-plane,
  be moved to the control-plane? This could include e.g. authorization to deliver traffic depending on the source,
  but also things like port numbers/ranges per source, etc.
  * Could this obsolete firewalls? What else would be necessary?
  * What do we mean when we say "authorize transit"?
* Could perfect forward secrecy DRKey be useful, and should we research it?
  * What would be the trust model? Do end-users trust their ASes to ephemerally create personal keys?
  * What would be the attacker model?
  * Which use cases are relevant?

For more info: {{I-D.garciapardo-drkey}}.

## SCMP Authentication
In SCION, we would like to have SCMP (SCION Control Message Protocol) include authentication for
some of the message types, e.g. the interface down type, as it would affect the path choices that the
endpoint, and even the source AS, can make.

We propose to use DRKey as the mechanism to use to derive the authentication key,
where the fast path would be on the infrastructure side (e.g. the border router in the case of an
interface down type of message), and the slow side being on the intended endpoint destination
for that SCMP message (e.g. the endpoint receiving the SCMP interface down message).
However, we have identified a number of possible issues (not comprehensive):

* Denial of Service/Capability Attacks: If an endpoint receives (too) many SCMP messages,
  it will need (too) many resources just to authenticate their origin.
  Most of these messages could just be sent to the endpoint to exhaust its processing capacity.

* Sending an SCMP message in certain cases might be an amplification factor:
  If a border router sends an SCMP message (e.g. interface down) on all cases, even with small packets,
  there is the risk of having that border router sending a lot of traffic to
  a possibly unintended recipient, e.g. when the packet is not source validated.

## Proof of transit

FABRID {{KRAHENBUHL2023}} and EPIC {{LEGNER2020}}.

## NAT

At this moment, the SCION implementation is not compatible out-of-the-box with NAT'ed devices, regardless of whether these devices are end-hosts, or even running SCION services. This is due to the (UDP-IP) underlay being modified by the NAT mechanism, but not the internal destination SCION address. Although this does not concern the SCION protocols themselves, we want to check that this will not be a problem.
Critically, the SCION header needs to contain the SRC address as seen by the border router so that the border router can forward incoming response packets to the correct NAT device and port.

Possible solutions:

* With IPv6 underlay, this problem disappears. // TODO Clarify why it disappears? IS the idea that we can remove NATs if everyone would use IPv6?
* Introduce a mechanism so that the SCION border router can report the NATed address to an endpoint (similar to a STUN server).

# Dataplane stability

## Link load balancing

Links may get overloaded because the SCION routing system fails to distribute load properly over different links. New/different links might be underutilized.

If links become overloaded, there are several ways to handle that. Non comprehensively:

* Squeeze: send an SCMP message to trigger end-hosts to use an alternative path
* Steer: send and SCMP to trigger users to ask control server for a better path
* Reduce: hand over very short lived paths, let the end-hosts wait for the path to expire so that they request new paths and (hopefully) decide on a different path.
* Recommend: let the end-hosts know which paths are recommended by the AS at this time.

If a link has good properties, many AS will disseminate segments, therefore paths that go through this link and the link may become overloaded. See Simon Scherrer's work on Braess Paradox.

Either there needs to be some constant control by all clients to not choose the best theoretical path, but the one that works best. Or we need to find a way that control servers do not disseminate “good” links to all end-hosts.

The current consensus is that end-hosts can use multi-pathing and “automatically” converge on the best path, i.e. creating an equilibrium. Again, see Simon Scherrer's work on Braess Paradox.


## Reverse Path Refreshment

When a client contacts a server, it is usually understood that it wants the server to use the reverse path to answer back. It the server uses that path for a long period of time, the path will eventually expire. How to standardize the process of refreshment?

* The server must ask the control server for a path, regardless of the client's policy.
* The client (somehow) sends a new packet with a new path, prompting the server to use this path from now on.

There are some nuances: Usually the server's API will store the initial address of the client to be used through all the session. We might need to take this into account.

A related question: how long before expiration should we still use a path? How do we handle that?

Do we actually need to solve this reverse path refresh problem?

* CONTRA: It is probably rare that a server needs to send data for a long time without the application layer protocol requiring the client to ever answer back.
* PRO: The client may happen to have an old-ish path. If we can't refresh, the client always needs to consider whether a path is valid "long enough", which might only be possible to guess.
* CONTRA: Sending keep-alives sounds like a connection based protocol. It alo means we need to figure out when to stop sending keep alives.
* CONTRA: It may be better to solve this in the application layer or in the overlay protocol, where we we know more about
  potential length of the session, or whether this is a singular request/answer type of exchange, or whether more frequent keep-alives
  are anyway required.


## Signalling faulty segments

Faulty segments are segments that do not work as advertised, i.e. they are either physically faulty
(broken link, high packet loss, jitter, ...) or come with faulty metadata, suggesting too few hops, too low latency,
too much bandwith, or similar problems.
The fault may be caused by a technical problem (e.g. broken link) or by a malicious adversary.

An example for a malicious adversary is the "wormhole" attack, see {{I-D.scion-cp}}, where, an AS may be coaxed to
disseminate a faulty segment. How do we recover from faulty segments?
Currently only endpoints may realize that a segment does not work as advertised, either via SCMP errors or simply by traffic degradation.
This would be a possible sequence of events:

* An endpoint realizes that a segment is faulty
* An endpoint needs to signal to its local AS that a segment is faulty
* Local AS needs to signal its CORE AS that a segment is faulty
* The CORE AS needs to:
  * change policy to exclude faulty segments AND/OR
  * signal other COREs and ISDs to stop delivering the segment (they only deliver 5 each, so any faulty segment shoud be avoided)

### Implications

Besides general service degradation, a lack of recovery can worsen the impact of a wormhole attack {{wormhole-attack}}.

### Mitigation

* An AS could monitor traffic for SCMP errors, however this works only if these errors are actually generated and forwarded.
* Endpoints need a way to signal faulty segments to ASes. ASes need a way to signal faulty ASes to other ASes (e.g.
core ASes or ASes in other ISDs).
* ASes need adaptive beacon analysis algorithms that allow excluding specific beacons, e.g. beacons that have
  known malicious ASes on path.
* For swift recovery, it would be useful if ASes could communicate the faultiness of faulty segments.


<!--
# Hummingbird / QoS

* How many QoS flows to support at core routers?
* How does QoS interact with Net Neutrality?
* What proof of transit (or forwarding failure detection) is needed or wanted?
* What time synchronization precision should we expect at the border router level of every AS? How far can we go realistically?
-->

# Interfaces for Path Awareness

* IPv6 in the Data Plane
* SCION-IP translation
* How can we interface with QUIC Multipath {{I-D.ietf-quic-multipath}}?

# Implications of Path Awareness for the Transport and Application Layers

To be discussed

# Naming

To be discussed

# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
