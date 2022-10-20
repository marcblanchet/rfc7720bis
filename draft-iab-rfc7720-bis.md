---
title: DNS Root Name Service Protocol and Deployment Requirements
abbrev: RSS Requirements
docname: draft-rssac-caucus-rfc7720bis-00

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
   ins: W. Hardaker
   name: Wes Hardaker
   org: USC/ISI
   email: ietf@hardakers.net
 -
   ins: M. Kosters
   name: Mark Kosters
   org: Network Solutions
   email: markk@netsol.com

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
The protocol and deployment requirements for the DNS root name service are defined in this document.
Operational requirements are out of scope.

--- middle

# Introduction

{{RFC2870}} discusses protocol and operational requirements for root
name servers for the Internet's domain name system (DNS) protocol
{{RFC1035}}.  Since its publication, both protocol and operational
requirements have evolved.  It makes more sense now to separate the
two sets of requirements into two separate documents.  This document
only defines the protocol requirements and some deployment
requirements.  The operational requirements that were defined in RFC
2870 have been removed.  Operational requirements are now defined by
the Root Server System Advisory Committee of ICANN and are documented
in {{RSSAC-001}}.

The root servers are authoritative servers of the unique {{RFC2826}}
root zone (".") {{ROOTZONE}}.  They currently also serve the root-
servers.net zone.  Some also serve the zone for the .arpa top-level
domain {{ARPAZONE}} {{RFC3172}}.  This document describes the external
interface of the root name servers from a protocol viewpoint of the
service.  It specifies basic requirements for the Internet that DNS
clients meet when interacting with a root name service over the
public Internet.

The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”,
“SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “NOT RECOMMENDED”, “MAY”,
and “OPTIONAL” in this document are to be interpreted as described in
{{RFC8174}} when, and only when, they appear in all capitals, as shown here.


## Relationship to RFC 2870

This document obsoletes {{RFC2870}}.

This document and {{RSSAC-001}} together functionally replace
{{RFC2870}}.

# Protocol Requirements

This section describes the minimum high-level protocol requirements.
Operative details are documented in {{RSSAC-001}}.

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
name service is a key component of the Internet architecture and play
a key role into the overall security of the Internet {{RFC2826}}.
Specific security considerations on the DNS protocols are discussed
in their respective specifications.  The security considerations on
the operational side of the root name servers are discussed in
{{RSSAC-001}}.

--- back

# Acknowledgements

This document was prepared by the ICANN RSSAC Caucus with participation of many Caucus members.

Some text was taken from {{RFC2870}}.

The editors of this document would like to sincerely thank the following individuals for valuable
contributions to the text of {{RFC7720}}:
Andrew Sullivan, Simon Perreault, Jean-Philippe Dionne, Dave Thaler, Russ Housley,
Alissa Cooper, Joe Abley, Joao Damas, Daniel Karrenberg, Jacques Latour, Eliot Lear,
Bill Manning, David Conrad, Paul Hoffman, Terry Manderson, Jari Arkko, and Mark
Andrews.

