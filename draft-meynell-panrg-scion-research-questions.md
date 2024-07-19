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
  RFC9217: # Current Open Questions in PAN
  RFC9000: # QUIC
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
  RFC9460:
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

  TABAEIAGHDAEI2023:
    title: "Inter-domain Routing with Extensible Criteria"
    date: 2023
    target: https://netsec.ethz.ch/publications/papers/IREC_arXiv.pdf
    author:
      -
        ins: S. Tabaeiaghdaei
        name: Seyedali Tabaeiaghdaei
        org: ETH Zürich
      -
        ins: M. Wyss
        name: Marc Wyss
        org: ETH Zürich
      -
        ins: G. Giuliari
        name: Giacomo Giuliari
        org: ETH Zürich
      -
        ins: J. van Bommel
        name: Jelte van Bommel
        org: ETH Zürich
      -
        ins: A. N. Zehmakan
        name: Ahad N. Zehmakan
        org: Australian National University
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

SCION is an inter-domain network architecture. Its core components, as deployed by some of its early adopters, are specified in {{I-D.scion-dataplane}}, {{I-D.scion-cppki}}, {{I-D.scion-cp}} which are currently under ISE review.

The goal of this draft is to explore how SCION and its early deployments try to address open research questions in {{RFC9217}}. Specifically, there are still many open areas of research around path-aware networking, where SCION with its early deployment experiences and research efforts can provide a contribution. This can also be a starting point for discussions around long-term protocol evolution.

This draft assumes the reader is familiar with some of the fundamental concepts defined in the components specification.

**Note:** This is the very first version of the SCION research questions draft, and it merely contains a skeleton of potential topics to be further discussed in this draft. Any feedback is welcome and much appreciated. Thanks!


# Conventions and Definitions

{::boilerplate bcp14-tagged}

# Discovery, Distribution, and Trustworthiness of Path Properties

## ISD, AS identity

The SCION protocol specifies 16 bits and 48 bits to identify the ISD and AS respectively.
This identification is used at the data-plane level, in every packet to fully address the sender and receiver, and at the control-plane level, to identify the PCB sender and hops.

Whilst 48 bits for the AS will accommodate up to 2.81475e14 assignments which is likely to be more than sufficient for the future, using 16 bits for the ISD only offers 65,536 possible assignments. Further investigation on whether this is sufficient is required.

The following questions arise: (not comprehensive)

* How many ASes do we expect in the SCION network model?
* Can one AS belong to many ISDs?
* Are AS numbers unique themselves, or only unique in combination with an ISD?
* How many ISDs do we expect?
* What is the ontology of an ISD?
  * Per geographic area?
  * Per legal jurisdiction?
  * Per capacity tier?
  * Per "type"? (meaning: any grouping that makes sense to their members)
  * Possible combinations of any previous "types"?
* Note that, to achieve global connectivity, ISDs require core links to other ISDs.
  This reduces the number of ISDs to those that have core ASes that can directly
  connect to core ASes in other ISDs.
  The number of ISDs is still super-exponential asymptotically.


## Beacon Selection Policies

Path discovery between SCION ASes relies on Path Construction Beacons (PCBs). In core beaconing PCBs are propagated omnidirectionally, unless this would cause a loop or exceed the maximum _path length_.
A core AS selects a small number of paths to/from other core ASes, based on its beacon selection policy. It then propagates valid and policy compliant paths to neighbor ASes. The number of propagated beacons is limited to the _best PCBs set size_, in order to avoid that the number of paths (and beacons) grows exponentially with core network size.

Some potential questions are:
* Limiting the number of beacons to a _best PCBs set size_ per AS results in a partial view of the network being available to endpoints. To what point this affects endpoint's path-selection possibilities?
* what is a good, practical, general purpose policy, that can fulfill conflicting requirements of both operators and endpoints, as highlighted in section 2.7 of {{RFC9217}}?
* What are the desirable path properties (e.g. diversity, PCB Expiration Time, how recently the same PCBs was forwarded before).

<!--
Since a path may expire after an hour or so and because expiration is not the only factor, an AS will typically start
resending the same beacons in less than an hour (i.e. the typical expiration time).

This means the total number of different PCBs that an AS will receive from a given neighbor is e.g.
5 per minute * 30 minute = 150 paths.

Most likely, an AS will receive PCBs originating from a given source from several neighbors, although these are likely to be
very similar. They are likely to have the same tail and only differ in the few last added hops, i.e. the immediate neighbors.

As a result, an AS will probably have only little more than 150 paths to a given remote AS.


This is likely sufficient for most applications, but is far from a complete view of the network.

This can be problematic:

* Massive multipathing: endpoints may not be able to use the theoretically best paths.
* Unusual path policies, such as geofencing, may not be fulfillable by the limited number of paths on offer.
-->



## DNS Service Binding (SVCB)

The DNS Service Binding {{?RFC9460, Section 14.3}} allows a dedicated SCION Service Parameter to be specified.

Service Parameters allow the specification of alternative IP addresses or other parameters (such as ISD/AS numbers) for a given URL.
This would be more elegant than using DNS TXT records.

Example of current entry:

    $ dig +short ethz.ch TXT  | grep scion
    "x-sciondiscovery=8041"
    "scion=64-2:0:9,129.132.230.98"


With SVCB this may look like this for https:

    dig +short https ethz.ch
    1 . alpn="h2" scion=64-2:0:9,129.132.230.98

SVCB is also planned to be supported by Happy Eyeballs v3 {{?I-D.draft-pauly-v6ops-happy-eyeballs-v3-01}}.


## Segment Dissemination

Control services may return a large number of path segments for some queries.
This can cost considerable bandwidth while at the same time
overloading clients with an unnecessarily large numbers of segments.

* This problem may be more acute in ASes with many endpoints (e.g. IoT),
or for resource-constrained endpoints.
* Getting a full path to a remote endpoint may require three queries to the control service.

There are multiple possible and independent solution steps here:

* Predefine some policies that can be resolved by the control plane, e.g. ANY, BEST_LATENCY, BEST_BANDWIDTH, BEST_PRICE,
BEST_CO2. For these, the control plane could simply calculate 5-10 compliant paths and return these.
Moreover these could be cached for commonly requested remote ASes.
If a user requires a custom policy they can still resort to requesting actual segments.
* Caching of paths. An open question concerns when a control service should return a chached path, versus performing a recursive path lookup.

An example including the number of core segments between different ISDs as of 2024-07-12 in the SCION production network is shown in [](#segment-count-example).

| src ISD | dst ISD | segments returned |
| ------: + ------: + :---------------: |
| 64      | 64      | 337               |
| 64      | 65      | 240               |
| 64      | 67      | 60                |
{: #segment-count-example title="core segment count examples"}

## Periodic beacon propagation
The SCION control plane protocol specifies that beacons should be propagated periodically.
Is this really necessary?

  * For path freshness, only the initial AS emitting the PCB needs to originate beacons periodically,
  and others can disseminate immediately.
  * As response to link failures or availability of new paths, beacon services can respond instantly.

If no periodic propagation is necessary for path freshness or to respond to link failures,
the periodic propagation would only be used for the discovery of new paths at each interval,
enhancing the scalability and path diversity.

## Beacon optimization and extensibility
Communication requirements vary according to source, destination, and application.
Satisfying all these requirements either requires discovering all paths in the network,
or optimizing the creation of paths during the beaconing process.
Selecting the 5 shortest paths per destination for each beaconing period may not satisfy all requirements
that different applications, on different endpoints, and on different ASes, will have.
The beacon selection process, the criteria and metrics that they carry, and the adaptability
of them all have a strong impact in the traffic engineering of the individual ASes,
and of the inter-domain communication as a whole. See question 2.7 of {{RFC9217}}.

* What optimization functions should be applied to beacons and what metrics should be considered when propagating them ?
  Is the set of properties composed of path length, peering ASes, path disjointness, PCB last reception,
  and path lifetime enough?
* How do we extend the metrics with new dimensions, such as bandwidth, latency, geo-position, etc?
* Who should select these functions?
* How should the outcome of these functions be verified?
* How can multiple functions be applied concurrently, for different source and destination applications?
* How should end-ASes express their desired requirements to the inter-domain control plane?
* How do these requirements translate into concrete optimization functions?
* How would standardization of the functions look like?
* The functions changing over time:
  * How can optimization functions adapt to incorporate these changes?
  * How to achieve fast adaptation of optimization functions?
* See also: IREC {{TABAEIAGHDAEI2023}}


## Routing Policies and Traffic Engineering

Reduced adoption due to limited routing policy possibilities, such as a (core-)AS does not want to accept transit traffic unless it starts/ends in ASes with special properties. For example a GEANT AS does not want to allow transit traffic unless it originates or ends in another research and education AS.

One solution could be to add a “confirm full path”-flag to certain segments. If this flag is set, the full path (all segments) needs to authorized by all ASes that insist on authorizing it. This is obviously less scalable but may be viable for ASes that insist on such policies. This also allows for “secret” policies.

Collateral: this probably needs a data plane change. Conceptually, we have only a single resulting segment, and that segment needs to be used in full, e.g. no on-path trickery.

## DRKey
DRKey is a key distribution system that scales well with the number of endpoints in the network.
It relies on two things:

* Two sides of a key: a fast side, and a slow side. Sometimes called fast and slow side of the derivation.
  The ability of deriving a key very quickly on the fast side is necessary for most of its use cases.
* A grouping of endpoints (such as ASes): The pieces necessary to derive a key, namely the L1 keys,
  are communicated to each keystore at each grouping (e.g., a keystore per AS).

The questions related to DRKey are the following ones (not comprehensive):

* Do we want to have any possible authorization that is at the moment carried out at the data-plane to be moved to the control-plane? This could include e.g. authorization to deliver traffic depending on the source, but also information like port numbers/ranges per source, etc.
  * Could this obsolete firewalls? What else would be necessary?
  * What do we mean when we say "authorize transit"?
* Could perfect forward secrecy DRKey be useful, and should we research it?
  * What would be the trust model? Do end-users trust their ASes to ephemerally create personal keys?
  * What would be the attacker model?
  * Which use cases are relevant?

For more info: {{I-D.garciapardo-drkey}}.

## SCMP Authentication
In SCION, endpoints are responsible to select alternate paths in case of failure.
One approach to detect failures is to rely on signals from the network, such as SCMP (SCION Control Message Protocol) messages.
These signals must be authenticated in order to be trusted by endpoints. This reflects a question raised in section 2.7 of {{RFC9217}}.


One option is to use DRKey as the mechanism to use to derive the authentication key,
where the fast path would be on the infrastructure side (e.g. the border router in the case of an
interface down type of message), and the slow side being on the intended endpoint destination
for that SCMP message (e.g. the endpoint receiving the SCMP interface down message).
Another option is to leverage the control-plane PKI.

However, we have identified a number of possible issues (not comprehensive):

* Denial of Service/Capability Attacks: If an endpoint receives (too) many SCMP messages,
  it will need (too) many resources just to authenticate their origin.
  Most of these messages could just be sent to the endpoint to exhaust its processing capacity.

* Sending an SCMP message in certain cases might be an amplification factor:
  If a border router sends an SCMP message (e.g. interface down) on all cases, even with small packets,
  there is the risk of having that border router sending a lot of traffic to
  a possibly unintended recipient, e.g. when the packet is not source validated.
  In addition, validation may trigger additional requests for keys.

## Proof of transit

FABRID {{KRAHENBUHL2023}} and EPIC {{LEGNER2020}}.

## NAT

Currently, the SCION implementation is not compatible out-of-the-box with NAT'ed devices, regardless of whether these devices are end-hosts, or even running SCION services. This is due to the (UDP-IP) underlay being modified by the NAT mechanism, but not the internal destination SCION address. Although this does not concern the SCION protocols themselves, we want to check that this will not be a problem.
Critically, the SCION header needs to contain the SRC address as seen by the border router so that the border router can forward incoming response packets to the correct NAT device and port.

Possible solutions:

* With IPv6 underlay, this problem disappears. // TODO Clarify why it disappears? Is the idea that we can remove NATs if everyone would use IPv6?
* Introduce a mechanism so that the SCION border router can report the NATed address to an endpoint (similar to a STUN server).

# Dataplane stability

## Link load balancing

Links may get overloaded because the SCION distributed path selection process fails to distribute load properly over different links, resulting in uneven utilization.

There are several potential approaches to relieve an overloaded link:

* introduce explicit congestion notifications from routers to endpoints.
* optimize the path lookup process so that the control plane hands out paths that optimize load balancing.

<!--
If a link has good properties, many ASes will disseminate segments and therefore paths through this link to the extent link may become overloaded. See Simon Scherrer's work on Braess Paradox.

Either there needs to be some constant control by all clients to not choose the best theoretical path, but the one that works best, or there needs to be a mechanism whereby control plane do not disseminate “good” links to all end-hosts.

The current consensus is that end-hosts can use multi-pathing and “automatically” converge on the best path, i.e. creating an equilibrium. Again, see Simon Scherrer's work on Braess Paradox.
-->

## Reverse Path Refreshment

When a client and server communicate, return traffic should usually follow the same reverse path.
If the server uses that path for a long period of time, the path will eventually expire.
How should the server determine the path for return traffic and at which layer? How to avoid this being a vector pf path hijackings?

There are some relevant points for the discussion:

* In order to send data back to the client, the server needs to store the path locally
  (analogous to storing the client's 4-tuple in an TCP/IP scenario).

* More generally, if multiple paths are used to contact the server,
  which one of those would be used to reply? Should this be responsibility of the transport protocol,
  as in the case of QUIC-MP {{I-D.ietf-quic-multipath}}?

* How long before path expiration should the client and server still use a path?
  The client can choose from paths that will not expire in a short period of time,
  but it does not control for how long the server will attempt to use it (i.e.
  how long it will take the server to send the complete response).

### Proposed Solutions (not comprehensive)

* The server MUST ask the control plane for a path, regardless of the client's policy.
* The client SHOULD (somehow) send a new packet with a new path,
prompting the server to use this path from now on.
* The client and server agree, via a path policy specification,
  on which kinds of paths are okay for the server to use.
  This solution implies a standard specification of this path policy.
* Leave the solution to the application and transport layers.
  Transport protocols may require keep alive messages, or already support multiple paths.
  Applications should know for how long they are willing to read a response from a server.
  With this knowledge these two layers can easily determine when to send a new path
  (analogous to connection migration in QUIC {{RFC9000}}), so that the server is instructed
  to use it for the next replies.
* The server must ask the control plane for a path, regardless of the client's policy.
* The client (somehow) sends a new packet with a new path, prompting the server to use this path from now on.

There are some nuances: Usually the server's API will store the initial address of the client to be used through all the session.

A related question: how long before expiration should a path be used?

Is reverse path refresh a relevant problem?

* Contra: It is probably rare that a server needs to send data for a long time without the application layer protocol requiring the client to ever answer back.
* Pro: The client may happen to have an old-ish path. If we can't refresh, the client always needs to consider whether a path is valid "long enough", which might only be possible to guess.
* Contra: Sending keep-alives sounds like a connection based protocol. It also means we need to figure out when to stop sending keep-alives.
* Contra: It may be better to solve this in the application layer or in the overlay protocol, where we we know more about
  potential length of the session, whether this is a singular request/answer type of exchange, or whether more frequent keep-alives
  are required anyway.



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
