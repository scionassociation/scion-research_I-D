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


## Segment Dissemination

Control servers return a large number of path segments. This can cost considerable bandwidth / network egress while at the same time overloading clients with an unnecessarily large numbers of segments, mostly consisting of redundant information in terms of duplicate link and hops.

* This problem may be more problematic in ASes with many end hosts (e.g. IoT), or end hosts with little computing power or little spare bandwidth.
* Getting a full path to a remote endhost may require three round-trips with the control server.

There are multiple possible and independent solution steps here:

* Compression (idea suggested by Francois Wirz): Segments could be stored in a way that duplicate information (hops & links) is only stored once and the segments contain only references to the hops and links.
* Allow queries from start AS to end AS across multiple segments. This should be very easy to implement and would be compatible with the current wire protocol (protobuf).
  * This would reduce the number of round trips to one.
  * It would reduce the number of returned segments because only segments that actually connect to other segments would need to be returned.
* Predefine some policies that can be resolved by the control server, e.g. ANY, BEST_LATENCY, BEST_BANDWIDTH, BEST_PRICE, BEST_CO2. For these, a control server could simply calculate 5-10 good paths and return these. Moreover these could be cached for commonly requested remote ASs. If a user requires a custom policy they can still resort to requesting actual segments.

Doing path computation on the control server will initially increase computational cost. However, it would substantially decrease network egress. Caching of paths should reduce CPU cost, maybe even below the current cost for retrieving a large amount of segments from the local database and sending them over the network interface.

Examples for requesting CORE segments between different ISDs or within an ISD (as of 2024-07-12):

| src         | dst         | segments returned |
| ----------: + ----------: + :---------------: |
| 64-0:0:0    | 64-0:0:0    | 337               |
| 64-0:0:0    | 65-0:0:0    | 240               |
| 64-0:0:0    | 67-0:0:0    | 60                |
| 64-0:0:0    | 64-2:0:13   | 60                |
{: #segment-count-example title="CORE segment count examples"}


## Routing Policies and Traffic Engineering

Reduced adoption due to limited routing policy possibilities, such as a (core-)AS does not want to accept transit traffic unless it starts/ends in ASs with special properties. For example a GEANT AS does not want to allow transit traffic unless it originates or ends in another research AS.

One solution could be to add a “confirm full path”-flag to certain segments. If this flag is set, the full path (all segments) needs to authorized by all ASes that insist on authorizing it. This is obviously less scalable but may be viable for ASes that insist on such policies. This also allows for “secret” policies.

Collateral: this probably needs a data plane change. Conceptually, we have only a single resulting segment, and that segment needs to be used in full, e.g. no on-path trickery.

## DRKey
* Is forward-secrecy DRKey useful and should we develop it?
* What are the properties of the control-plane?
  * Do we want to have any authorization of the data-plane transit undertaken at this stage?
  * Would this obsolete firewalls?
  * What do we mean when we say "authorize transit"?

For more info: {{I-D.garciapardo-drkey}}.

## SCMP Authentication

## Proof of transit

FABRID {{KRAHENBUHL2023}} and EPIC {{LEGNER2020}}.

## NAT

At this moment, the SCION implementation is not compatible out-of-the-box with NAT'ed devices, regardless of whether these devices are end-hosts, or even running SCION services. This is due to the (UDP-IP) underlay being modified by the NAT mechanism, but not the internal destination SCION address. Although this does not concern the SCION protocols themselves, we want to check that this will not be a problem.
Critically, the SCION header needs to contain the SRC address as seen by the border router so that the border router can forward incoming response packets to the correct NAT device and port.

Possible solutions:

* With IPv6 underlay, this problem disappears. // TODO Clarify why it disappears? IS the idea that we can remove NATs if everyone would use IPv6?
* Introduce a mechanism so that the SCION border router can report the NATed address to an endhost (similar to a STUN server).

# Dataplane stability

## Link load balancing

Links may get overloaded because the SCION routing system fails to distribute load properly over different links. New/different links might be underutilized.

If links become overloaded, there are several ways to handle that. Non comprehensively:

* Squeeze: send an SCMP message to trigger end-hosts to use an alternative path
* Steer: send and SCMP to trigger users to ask CS for a better path
* Reduce: hand over very short lived paths, let the end-hosts wait for the path to expire so that they request new paths and (hopefully) decide on a different path.
* Recommend: let the end-hosts know which paths are recommended by the AS at this time.

If a link has good properties, many AS will disseminate segments, therefore paths that go through this link and the link may become overloaded. See Simon Scherrer's work on Braess Paradox.

Either there needs to be some constant control by all clients to not choose the best theoretical path, but the one that works best. Or we need to find a way that control servers do not disseminate “good” links to all end-hosts.

The current consensus is that end-hosts can use multi-pathing and “automatically” converge on the best path, i.e. creating an equilibrium. Again, see Simon Scherrer's work on Braess Paradox.


## Reverse Path Refreshment

When a client contacts a server, it is usually understood that it wants the server to use the reverse path to answer back. It the server uses that path for a long period of time, the path will eventually expire. How to standardize the process of refreshment?

* The server must ask the CS for a path, regardless of the client's policy.
* The client (somehow) sends a new packet with a new path, prompting the server to use this path from now on.

There are some nuances: Usually the server's API will store the initial address of the client to be used through all the session. We might need to take this into account.

A related question: how long before expiration should we still use a path? How do we handle that?

Do we actually need to solve this reverse path refresh problem?

* CONTRA: It is probably rare that a server needs to send data for a long time without the application layer protocol requiring the client to ever answer back.
* PRO: The client may happen to have an old-ish path. If we can't refresh, the client always needs to consider whether a path is valid "long enough", which might only be possible to guess.
* CONTRA: Sending keep-alives sounds like a connection based protocol. It alo means we need to figure out when to stop sending keep-alives.
* CONTRA: It may be better to solve this in the application layer or in the overlay protocol, where we we know more about
  potential length of the session, or whether this is a singular request/answer type of exchange, or whether more frequent keep-alives
  are anyway required.


# Hummingbird / QoS

* How many QoS flows to support at core routers?
* How does QoS interact with Net Neutrality?
* What proof of transit (or forwarding failure detection) is needed or wanted?
* What time synchronization precision should we expect at the border router level of every AS? How far can we go realistically?

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
