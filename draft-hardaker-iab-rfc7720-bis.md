---
title: DNS Root Name Service Protocol and Deployment Requirements
abbrev: RSS Requirements
docname: draft-hardaker-iab-rfc7720-bis-00

stand_alone: true
v: 3
obsoletes: 7720

ipr: trust200902
kw: Internet-Draft
cat: bcp
consensus: true
submissionType: IETF

pi:
  toc: yes
  tocdepth: 4
  sortrefs: yes
  symrefs: yes

author:
 -
   ins: M Blanchet
   name: M Blanchet
   org: Viagenie
   email: Marc.Blanchet@viagenie.ca
 - 
   ins: L. Liman
   name: Lars-Johan Liman
   org: Netnod Internet Exchangen
   email: liman@netnod.se
 -
   ins: W. Hardaker
   name: Wes Hardaker
   org: USC/ISI
   email: ietf@hardakers.net

normative:
  RFC8174:
  
informative:
  RFC0768:
  RFC0791:
  RFC0793:
  RFC1035:
  RFC1122:
  RFC2181:
  RFC2460:
  RFC2870:
  RFC2826:
  RFC3172:
  RFC4035:
  RFC6891:
  RFC7720:
  RFC8976:
  RFC9120:
  ARPAZONE:
    title: .ARPA Zone Management
    author:
      name: IANA
    target: http://www.iana.org/domains/arpa
  ROOTZONE:
    title: Root Zone
    author:
      name: IANA
    target: https://www.iana.org/domains/root/files
  RSSAC-001:
    title: Service Expectations of Root Servers
    author:
      org: Root Server System Advisory Committee
    target: https://www.icann.org/en/system/files/files/rssac-001-root-service-expectations-04dec15-en.pdf
    date: 2015

--- abstract

The DNS root name service is a critical part of the Internet architecture.
The DNS root name service's DNS protocol and deployment requirements are defined in this document.
Operational requirements for the root name service are out of scope.

--- middle

# Introduction

This document co-exists with a corresponding operational requirements
document published by the Root Server System Advisory Committee of
ICANN in {{RSSAC-001}} or any subsequent version.  Although intricately
tied together, both of these documents may be updated at any time to
reflect required updates to the protocol, deployment and operational
requirements.  Further notes about the history of these documents is
discussed in {{history}}.


The root servers are authoritative servers of the unique {{RFC2826}}
root zone (".") {{ROOTZONE}}.  They currently also serve the root-
servers.net zone.  Some also serve the zone for the .arpa top-level
domain {{ARPAZONE}} {{RFC3172}}, although at the time of this writing
there are plans to move the service for the .arpa top-level domain to
different infrastructure {{RFC9120}}.

This document describes the external interface of the root name
servers from a protocol viewpoint of the service.  It specifies basic
requirements for the Internet that DNS clients meet when interacting
with a root name service over the public Internet.

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY",
and "OPTIONAL" in this document are to be interpreted as described in
{{RFC8174}} when, and only when, they appear in all capitals, as shown here.


## Relationship to RFC2870 and RFC7720

This document obsoletes both {{RFC2870}} and {{RFC7720}}.

# Protocol Requirements

This section describes the minimum high-level protocol requirements.

The root name service:

- MUST implement core DNS {{RFC1035}} and clarifications to the DNS
{{RFC2181}}.

- MUST support IPv4 {{RFC0791}} and IPv6 {{RFC2460}} transport of DNS
queries and responses.

- MUST support UDP {{RFC0768}} and TCP {{RFC0793}} transport of DNS
queries and responses.

- MUST generate checksums when sending UDP datagrams and MUST verify
checksums when receiving UDP datagrams containing a non-zero
checksum.

- MUST implement DNSSEC {{RFC4035}} as an authoritative name service.

- MUST implement extension mechanisms for DNS (EDNS(0)) {{RFC6891}}.

# Deployment Requirements

The root name service:

- MUST answer queries from any entity conforming to {{RFC1122}} with a
valid IP address.

- MUST serve the unique {{RFC2826}} root zone {{ROOTZONE}}.

# Security Considerations

This document does not specify a new protocol.  However, the root
name service is a key component of the Internet architecture and plays
a key role into the overall security of the Internet {{RFC2826}}.
Specific security considerations on the DNS protocols are discussed
in their respective specifications.  The security considerations on
the operational side of the root name servers are discussed in
the corresponding document published by RSSAC ({{RSSAC-001}} or a
subsequent version).

--- back

# Working version of this document

This document is being worked on within the following github repo.
Issues and pull requests are welcomed:

https://github.com/marcblanchet/rfc7720bis

# History

## Changes between RFC7720 and this document

Existing list of changes:

- Changed instances of RSSAC-001 to also include subsequent versions
- General restructuring to better document requirements vs a
  discussion of the document's history and changes

## Changes between RFC2870 and RFC7720

{{RFC2870}} originally discussed both the protocol and operational
requirements for root name servers for the Internet's domain name
system (DNS) protocol {{RFC1035}}.  Since its initial publication,
both protocol and operational requirements have evolved.  The protocol
requirements was later split into {{RFC7720}} and the operational
requirements was moved to {{RSSAC-001}} and published by ICANN's Root
Server System Advisory Committee (RSSAC).  These two documents
functionally replaced {{RFC2870}}.  Similarly, this document now
functionally replaces {{RFC7720}}.

As both of these requirement sets are expected to evolve over time,
the authors of both document sets hope to always keep them roughly in
synchronization.  However, the latest version of both of these two
documents should be consider the most recent set of requirements
regardless of whether they were published together or separately.


# Acknowledgements

This document was prepared by the ICANN RSSAC Caucus with participation of many Caucus members.

Much of this text is a rearrangement and restatement of {{RFC7720}},
which itself contains text was taken from {{RFC2870}}.

The editors of this document would like to sincerely thank the following individuals for valuable
contributions to the text of {{RFC7720}}:
Andrew Sullivan, Simon Perreault, Jean-Philippe Dionne, Dave Thaler, Russ Housley,
Alissa Cooper, Joe Abley, Joao Damas, Daniel Karrenberg, Jacques Latour, Eliot Lear,
Bill Manning, David Conrad, Paul Hoffman, Terry Manderson, Jari Arkko, and Mark
Andrews.

