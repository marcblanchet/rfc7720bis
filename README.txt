



Network Working Group                                        W. Hardaker
Internet-Draft                                                   USC/ISI
Obsoletes: 7720 (if approved)                               . M Blanchet
Intended status: Best Current Practice                          Viagenie
Expires: 23 April 2023                                          L. Liman
                                               Netnod Internet Exchangen
                                                         20 October 2022


       DNS Root Name Service Protocol and Deployment Requirements
                        draft-iab-rfc7720-bis-00

Abstract

   The DNS root name service is a critical part of the Internet
   architecture.  The protocol and deployment requirements for the DNS
   root name service are defined in this document.  Operational
   requirements are out of scope.

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

   This Internet-Draft will expire on 23 April 2023.

Copyright Notice

   Copyright (c) 2022 IETF Trust and the persons identified as the
   document authors.  All rights reserved.











Hardaker, et al.          Expires 23 April 2023                 [Page 1]

Internet-Draft              RSS Requirements                October 2022


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
     1.1.  Relationship to RFC 2870  . . . . . . . . . . . . . . . .   3
   2.  Protocol Requirements . . . . . . . . . . . . . . . . . . . .   3
   3.  Deployment Requirements . . . . . . . . . . . . . . . . . . .   3
   4.  Security Considerations . . . . . . . . . . . . . . . . . . .   4
   5.  References  . . . . . . . . . . . . . . . . . . . . . . . . .   4
     5.1.  Normative References  . . . . . . . . . . . . . . . . . .   4
     5.2.  Informative References  . . . . . . . . . . . . . . . . .   4
   Appendix A.  Acknowledgements . . . . . . . . . . . . . . . . . .   5
   Authors' Addresses  . . . . . . . . . . . . . . . . . . . . . . .   6

1.  Introduction

   [RFC2870] discusses protocol and operational requirements for root
   name servers for the Internet's domain name system (DNS) protocol
   [RFC1035].  Since its publication, both protocol and operational
   requirements have evolved.  It makes more sense now to separate the
   two sets of requirements into two separate documents.  This document
   only defines the protocol requirements and some deployment
   requirements.  The operational requirements that were defined in RFC
   2870 have been removed.  Operational requirements are now defined by
   the Root Server System Advisory Committee of ICANN and are documented
   in [RSSAC-001].

   The root servers are authoritative servers of the unique [RFC2826]
   root zone (".") [ROOTZONE].  They currently also serve the root-
   servers.net zone.  Some also serve the zone for the .arpa top-level
   domain [ARPAZONE] [RFC3172].  This document describes the external
   interface of the root name servers from a protocol viewpoint of the
   service.  It specifies basic requirements for the Internet that DNS
   clients meet when interacting with a root name service over the
   public Internet.








Hardaker, et al.          Expires 23 April 2023                 [Page 2]

Internet-Draft              RSS Requirements                October 2022


   The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
   "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and
   "OPTIONAL" in this document are to be interpreted as described in
   [RFC8174] when, and only when, they appear in all capitals, as shown
   here.

1.1.  Relationship to RFC 2870

   This document obsoletes [RFC2870].

   This document and [RSSAC-001] together functionally replace
   [RFC2870].

2.  Protocol Requirements

   This section describes the minimum high-level protocol requirements.
   Operative details are documented in [RSSAC-001].

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

3.  Deployment Requirements

   The root name service:

   *  MUST answer queries from any entity conforming to [RFC1122] with a
      valid IP address.

   *  MUST serve the unique [RFC2826] root zone [ROOTZONE].






Hardaker, et al.          Expires 23 April 2023                 [Page 3]

Internet-Draft              RSS Requirements                October 2022


4.  Security Considerations

   This document does not specify a new protocol.  However, the root
   name service is a key component of the Internet architecture and play
   a key role into the overall security of the Internet [RFC2826].
   Specific security considerations on the DNS protocols are discussed
   in their respective specifications.  The security considerations on
   the operational side of the root name servers are discussed in
   [RSSAC-001].

5.  References

5.1.  Normative References

   [RFC8174]  Leiba, B., "Ambiguity of Uppercase vs Lowercase in RFC
              2119 Key Words", BCP 14, RFC 8174, DOI 10.17487/RFC8174,
              May 2017, <https://www.rfc-editor.org/info/rfc8174>.

5.2.  Informative References

   [ARPAZONE] IANA, ., ".ARPA Zone Management", n.d.,
              <http://www.iana.org/domains/arpa>.

   [RFC0768]  Postel, J., "User Datagram Protocol", STD 6, RFC 768,
              DOI 10.17487/RFC0768, August 1980,
              <https://www.rfc-editor.org/info/rfc768>.

   [RFC0791]  Postel, J., "Internet Protocol", STD 5, RFC 791,
              DOI 10.17487/RFC0791, September 1981,
              <https://www.rfc-editor.org/info/rfc791>.

   [RFC0793]  Postel, J., "Transmission Control Protocol", RFC 793,
              DOI 10.17487/RFC0793, September 1981,
              <https://www.rfc-editor.org/info/rfc793>.

   [RFC1035]  Mockapetris, P., "Domain names - implementation and
              specification", STD 13, RFC 1035, DOI 10.17487/RFC1035,
              November 1987, <https://www.rfc-editor.org/info/rfc1035>.

   [RFC1122]  Braden, R., Ed., "Requirements for Internet Hosts -
              Communication Layers", STD 3, RFC 1122,
              DOI 10.17487/RFC1122, October 1989,
              <https://www.rfc-editor.org/info/rfc1122>.

   [RFC2181]  Elz, R. and R. Bush, "Clarifications to the DNS
              Specification", RFC 2181, DOI 10.17487/RFC2181, July 1997,
              <https://www.rfc-editor.org/info/rfc2181>.




Hardaker, et al.          Expires 23 April 2023                 [Page 4]

Internet-Draft              RSS Requirements                October 2022


   [RFC2460]  Deering, S. and R. Hinden, "Internet Protocol, Version 6
              (IPv6) Specification", RFC 2460, DOI 10.17487/RFC2460,
              December 1998, <https://www.rfc-editor.org/info/rfc2460>.

   [RFC2826]  Internet Architecture Board, "IAB Technical Comment on the
              Unique DNS Root", RFC 2826, DOI 10.17487/RFC2826, May
              2000, <https://www.rfc-editor.org/info/rfc2826>.

   [RFC2870]  Bush, R., Karrenberg, D., Kosters, M., and R. Plzak, "Root
              Name Server Operational Requirements", RFC 2870,
              DOI 10.17487/RFC2870, June 2000,
              <https://www.rfc-editor.org/info/rfc2870>.

   [RFC3172]  Huston, G., Ed., "Management Guidelines & Operational
              Requirements for the Address and Routing Parameter Area
              Domain ("arpa")", BCP 52, RFC 3172, DOI 10.17487/RFC3172,
              September 2001, <https://www.rfc-editor.org/info/rfc3172>.

   [RFC4035]  Arends, R., Austein, R., Larson, M., Massey, D., and S.
              Rose, "Protocol Modifications for the DNS Security
              Extensions", RFC 4035, DOI 10.17487/RFC4035, March 2005,
              <https://www.rfc-editor.org/info/rfc4035>.

   [RFC6891]  Damas, J., Graff, M., and P. Vixie, "Extension Mechanisms
              for DNS (EDNS(0))", STD 75, RFC 6891,
              DOI 10.17487/RFC6891, April 2013,
              <https://www.rfc-editor.org/info/rfc6891>.

   [RFC7720]  Blanchet, M. and L-J. Liman, "DNS Root Name Service
              Protocol and Deployment Requirements", BCP 40, RFC 7720,
              DOI 10.17487/RFC7720, December 2015,
              <https://www.rfc-editor.org/info/rfc7720>.

   [ROOTZONE] IANA, ., "Root Zone", n.d.,
              <https://www.iana.org/domains/root/files>.

   [RSSAC-001]
              Root Server System Advisory Committee, "Service
              Expectations of Root Servers", 2015,
              <https://www.icann.org/en/system/files/files/rssac-001-
              root-service-expectations-04dec15-en.pdf>.

Appendix A.  Acknowledgements

   This document was prepared by the ICANN RSSAC Caucus with
   participation of many Caucus members.

   Some text was taken from [RFC2870].



Hardaker, et al.          Expires 23 April 2023                 [Page 5]

Internet-Draft              RSS Requirements                October 2022


   The editors of this document would like to sincerely thank the
   following individuals for valuable contributions to the text of
   [RFC7720]: Andrew Sullivan, Simon Perreault, Jean-Philippe Dionne,
   Dave Thaler, Russ Housley, Alissa Cooper, Joe Abley, Joao Damas,
   Daniel Karrenberg, Jacques Latour, Eliot Lear, Bill Manning, David
   Conrad, Paul Hoffman, Terry Manderson, Jari Arkko, and Mark Andrews.

Authors' Addresses

   Wes Hardaker
   USC/ISI

   Email: ietf@hardakers.net


   M Blanchet
   Viagenie

   Email: Marc.Blanchet@viagenie.ca


   Lars-Johan Liman
   Netnod Internet Exchangen

   Email: liman@netnod.se


























Hardaker, et al.          Expires 23 April 2023                 [Page 6]
