



Network Working Group                                        M. Blanchet
Internet-Draft                                                  Viagenie
Obsoletes: 7720 (if approved)                                   L. Liman
Intended status: Best Current Practice         Netnod Internet Exchangen
Expires: 18 August 2023                                      W. Hardaker
                                                                 USC/ISI
                                                        14 February 2023


       DNS Root Name Service Protocol and Deployment Requirements
                   draft-hardaker-iab-rfc7720-bis-00

Abstract

   The DNS root name service is a critical part of the Internet
   architecture.  The DNS root name service's DNS protocol and
   deployment requirements are defined in this document.  Operational
   requirements for the root name service are out of scope.

Status of This Memo

   This Internet-Draft is submitted in full conformance with the
   provisions of BCP 78 and BCP 79.

   Internet-Drafts are working documents of the Internet Engineering
   Task Force (IETF).  Note that other groups may also distribute
   working documents as Internet-Drafts.  The list of current Internet-
   Drafts is at https://datatracker.ietf.org/drafts/current/.

   Internet-Drafts are draft documents valid for a maximum of six months
   and may be updated, replaced, or obsoleted by other documents at any
   time.  It is inappropriate to use Internet-Drafts as reference
   material or to cite them other than as "work in progress."

   This Internet-Draft will expire on 18 August 2023.

Copyright Notice

   Copyright (c) 2023 IETF Trust and the persons identified as the
   document authors.  All rights reserved.











Blanchet, et al.         Expires 18 August 2023                 [Page 1]

Internet-Draft              RSS Requirements               February 2023


   This document is subject to BCP 78 and the IETF Trust's Legal
   Provisions Relating to IETF Documents (https://trustee.ietf.org/
   license-info) in effect on the date of publication of this document.
   Please review these documents carefully, as they describe your rights
   and restrictions with respect to this document.  Code Components
   extracted from this document must include Simplified BSD License text
   as described in Section 4.e of the Trust Legal Provisions and are
   provided without warranty as described in the Simplified BSD License.

Table of Contents

   1.  Introduction  . . . . . . . . . . . . . . . . . . . . . . . .   2
     1.1.  Relationship to RFC2870 and RFC7720 . . . . . . . . . . .   3
   2.  Protocol Requirements . . . . . . . . . . . . . . . . . . . .   3
   3.  Deployment Requirements . . . . . . . . . . . . . . . . . . .   3
   4.  Security Considerations . . . . . . . . . . . . . . . . . . .   4
   5.  References  . . . . . . . . . . . . . . . . . . . . . . . . .   4
     5.1.  Normative References  . . . . . . . . . . . . . . . . . .   4
     5.2.  Informative References  . . . . . . . . . . . . . . . . .   4
   Appendix A.  History  . . . . . . . . . . . . . . . . . . . . . .   6
   Appendix B.  Acknowledgements . . . . . . . . . . . . . . . . . .   6
   Authors' Addresses  . . . . . . . . . . . . . . . . . . . . . . .   6

1.  Introduction

   This document co-exists with a corresponding operational requirements
   document published by the Root Server System Advisory Committee of
   ICANN in [RSSAC-001] or any subsequent version.  Although intricately
   tied together, both of these documents may be updated at any time to
   reflect required updates to the protocol, deployment and operational
   requirements.  Further notes about the history of these documents is
   discussed in Appendix A.

   The root servers are authoritative servers of the unique [RFC2826]
   root zone (".") [ROOTZONE].  They currently also serve the root-
   servers.net zone.  Some also serve the zone for the .arpa top-level
   domain [ARPAZONE] [RFC3172], although at the time of this writing
   there are plans to move the service for the .arpa top-level domain to
   different infrastructure [RFC9120].

   This document describes the external interface of the root name
   servers from a protocol viewpoint of the service.  It specifies basic
   requirements for the Internet that DNS clients meet when interacting
   with a root name service over the public Internet.







Blanchet, et al.         Expires 18 August 2023                 [Page 2]

Internet-Draft              RSS Requirements               February 2023


   The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
   "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and
   "OPTIONAL" in this document are to be interpreted as described in
   [RFC8174] when, and only when, they appear in all capitals, as shown
   here.

1.1.  Relationship to RFC2870 and RFC7720

   This document obsoletes both [RFC2870] and [RFC7720].

2.  Protocol Requirements

   This section describes the minimum high-level protocol requirements.

   The root name service:

   *  MUST implement core DNS [RFC1035] and clarifications to the DNS
      [RFC2181].

   *  MUST support IPv4 [RFC0791] and IPv6 [RFC2460] transport of DNS
      queries and responses.

   *  MUST support UDP [RFC0768] and TCP [RFC0793] transport of DNS
      queries and responses.

   *  MUST generate checksums when sending UDP datagrams and MUST verify
      checksums when receiving UDP datagrams containing a non-zero
      checksum.

   *  MUST implement DNSSEC [RFC4035] as an authoritative name service.

   *  MUST implement extension mechanisms for DNS (EDNS(0)) [RFC6891].

   *  MUST support distributing Message Digests for DNS Zones [RFC8976].

   *  MAY support validating Message Digests for DNS Zones [RFC8976].

3.  Deployment Requirements

   The root name service:

   *  MUST answer queries from any entity conforming to [RFC1122] with a
      valid IP address.

   *  MUST serve the unique [RFC2826] root zone [ROOTZONE].






Blanchet, et al.         Expires 18 August 2023                 [Page 3]

Internet-Draft              RSS Requirements               February 2023


4.  Security Considerations

   This document does not specify a new protocol.  However, the root
   name service is a key component of the Internet architecture and
   plays a key role into the overall security of the Internet [RFC2826].
   Specific security considerations on the DNS protocols are discussed
   in their respective specifications.  The security considerations on
   the operational side of the root name servers are discussed in the
   corresponding document published by RSSAC ([RSSAC-001] or a
   subsequent version).

5.  References

5.1.  Normative References

   [RFC8174]  Leiba, B., "Ambiguity of Uppercase vs Lowercase in RFC
              2119 Key Words", BCP 14, RFC 8174, DOI 10.17487/RFC8174,
              May 2017, <https://www.rfc-editor.org/rfc/rfc8174>.

5.2.  Informative References

   [ARPAZONE] IANA, ".ARPA Zone Management", n.d.,
              <http://www.iana.org/domains/arpa>.

   [RFC0768]  Postel, J., "User Datagram Protocol", STD 6, RFC 768,
              DOI 10.17487/RFC0768, August 1980,
              <https://www.rfc-editor.org/rfc/rfc768>.

   [RFC0791]  Postel, J., "Internet Protocol", STD 5, RFC 791,
              DOI 10.17487/RFC0791, September 1981,
              <https://www.rfc-editor.org/rfc/rfc791>.

   [RFC0793]  Postel, J., "Transmission Control Protocol", RFC 793,
              DOI 10.17487/RFC0793, September 1981,
              <https://www.rfc-editor.org/rfc/rfc793>.

   [RFC1035]  Mockapetris, P., "Domain names - implementation and
              specification", STD 13, RFC 1035, DOI 10.17487/RFC1035,
              November 1987, <https://www.rfc-editor.org/rfc/rfc1035>.

   [RFC1122]  Braden, R., Ed., "Requirements for Internet Hosts -
              Communication Layers", STD 3, RFC 1122,
              DOI 10.17487/RFC1122, October 1989,
              <https://www.rfc-editor.org/rfc/rfc1122>.

   [RFC2181]  Elz, R. and R. Bush, "Clarifications to the DNS
              Specification", RFC 2181, DOI 10.17487/RFC2181, July 1997,
              <https://www.rfc-editor.org/rfc/rfc2181>.



Blanchet, et al.         Expires 18 August 2023                 [Page 4]

Internet-Draft              RSS Requirements               February 2023


   [RFC2460]  Deering, S. and R. Hinden, "Internet Protocol, Version 6
              (IPv6) Specification", RFC 2460, DOI 10.17487/RFC2460,
              December 1998, <https://www.rfc-editor.org/rfc/rfc2460>.

   [RFC2826]  Internet Architecture Board, "IAB Technical Comment on the
              Unique DNS Root", RFC 2826, DOI 10.17487/RFC2826, May
              2000, <https://www.rfc-editor.org/rfc/rfc2826>.

   [RFC2870]  Bush, R., Karrenberg, D., Kosters, M., and R. Plzak, "Root
              Name Server Operational Requirements", RFC 2870,
              DOI 10.17487/RFC2870, June 2000,
              <https://www.rfc-editor.org/rfc/rfc2870>.

   [RFC3172]  Huston, G., Ed., "Management Guidelines & Operational
              Requirements for the Address and Routing Parameter Area
              Domain ("arpa")", BCP 52, RFC 3172, DOI 10.17487/RFC3172,
              September 2001, <https://www.rfc-editor.org/rfc/rfc3172>.

   [RFC4035]  Arends, R., Austein, R., Larson, M., Massey, D., and S.
              Rose, "Protocol Modifications for the DNS Security
              Extensions", RFC 4035, DOI 10.17487/RFC4035, March 2005,
              <https://www.rfc-editor.org/rfc/rfc4035>.

   [RFC6891]  Damas, J., Graff, M., and P. Vixie, "Extension Mechanisms
              for DNS (EDNS(0))", STD 75, RFC 6891,
              DOI 10.17487/RFC6891, April 2013,
              <https://www.rfc-editor.org/rfc/rfc6891>.

   [RFC7720]  Blanchet, M. and L-J. Liman, "DNS Root Name Service
              Protocol and Deployment Requirements", BCP 40, RFC 7720,
              DOI 10.17487/RFC7720, December 2015,
              <https://www.rfc-editor.org/rfc/rfc7720>.

   [RFC8976]  Wessels, D., Barber, P., Weinberg, M., Kumari, W., and W.
              Hardaker, "Message Digest for DNS Zones", RFC 8976,
              DOI 10.17487/RFC8976, February 2021,
              <https://www.rfc-editor.org/rfc/rfc8976>.

   [RFC9120]  Davies, K. and J. Arkko, "Nameservers for the Address and
              Routing Parameter Area ("arpa") Domain", RFC 9120,
              DOI 10.17487/RFC9120, October 2021,
              <https://www.rfc-editor.org/rfc/rfc9120>.

   [ROOTZONE] IANA, "Root Zone", n.d.,
              <https://www.iana.org/domains/root/files>.






Blanchet, et al.         Expires 18 August 2023                 [Page 5]

Internet-Draft              RSS Requirements               February 2023


   [RSSAC-001]
              Root Server System Advisory Committee, "Service
              Expectations of Root Servers", 2015,
              <https://www.icann.org/en/system/files/files/rssac-001-
              root-service-expectations-04dec15-en.pdf>.

Appendix A.  History

   [RFC2870] originally discussed both the protocol and operational
   requirements for root name servers for the Internet's domain name
   system (DNS) protocol [RFC1035].  Since its initial publication, both
   protocol and operational requirements have evolved.  The protocol
   requirements was later split into [RFC7720] and the operational
   requirements was moved to [RSSAC-001] and published by ICANN's Root
   Server System Advisory Committee (RSSAC).  These two documents
   functionally replaced [RFC2870].  Similarly, this document now
   functionally replaces [RFC7720].

   As both of these requirement sets are expected to evolve over time,
   the authors of both document sets hope to always keep them roughly in
   synchronization.  However, the latest version of both of these two
   documents should be consider the most recent set of requirements
   regardless of whether they were published together or separately.

Appendix B.  Acknowledgements

   This document was prepared by the ICANN RSSAC Caucus with
   participation of many Caucus members.

   Much of this text is a rearrangement and restatement of [RFC7720],
   which itself contains text was taken from [RFC2870].

   The editors of this document would like to sincerely thank the
   following individuals for valuable contributions to the text of
   [RFC7720]: Andrew Sullivan, Simon Perreault, Jean-Philippe Dionne,
   Dave Thaler, Russ Housley, Alissa Cooper, Joe Abley, Joao Damas,
   Daniel Karrenberg, Jacques Latour, Eliot Lear, Bill Manning, David
   Conrad, Paul Hoffman, Terry Manderson, Jari Arkko, and Mark Andrews.

Authors' Addresses

   M Blanchet
   Viagenie

   Email: Marc.Blanchet@viagenie.ca






Blanchet, et al.         Expires 18 August 2023                 [Page 6]

Internet-Draft              RSS Requirements               February 2023


   Lars-Johan Liman
   Netnod Internet Exchangen

   Email: liman@netnod.se


   Wes Hardaker
   USC/ISI

   Email: ietf@hardakers.net









































Blanchet, et al.         Expires 18 August 2023                 [Page 7]
