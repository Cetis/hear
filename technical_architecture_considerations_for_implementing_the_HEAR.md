Technical architecture considerations for implementing the HEAR
===============================================================

About this page
---------------

This page was created as part of a series of consultations CETIS
provided to the Burgess Implementation Steering Group for the UK Higher
Education Achievement Report in 2009.

Terms of Reference
------------------

This is a draft for discussion produced by JISC CETIS on behalf of JISC
for the HEAR implementation projects. Its content is non-normative and
for discussion.

Terms Used In This Document
---------------------------

-   **Relying Party**: An organisation that is the recipient of the HEAR
    and may wish to verify it; typically an employer or another HEI
-   **Issuing Institution**: The institution that issues a HEAR
-   **Electronic Signature**: A signature in digital form carrying
    legal authority.
-   **Digital Signature**: A cryptographic method that enables the
    recipient of a document to determine the sender, and whether its
    contents have been altered since it was signed.

Overview
--------

In this section we provide recommendations for the exchange of
achievement data, including access and verification considerations.

Sharing Mechanisms for HEAR documents
-------------------------------------

In this report we present five models for distributing and verifying
electronic HEAR documents. These models are to some extent complementary
and choice of a particular model over another does not present a
significant interoperability issue for employers or other third parties.
Instead institutions and vendors should consider the pros and cons of
each approach in terms of feasibility and desirability from a business
viewpoint.

### Type 1: Standalone Document Model

In this model the HEAR electronic document is created and signed by the
issuing institution, and then passed onto the graduate. The graduate may
then pass their HEAR to relying parties, who can verify whether the
document has been tampered with since it was issued by examining the
digital signature.

![Standalone Document Model diagram](hear_type1.png){width="554"
height="584"}

### Type 2: Public Online Document Model

In this model the HEAR electronic document is created and signed by the
issuing institution, but rather than passing it directly to the graduate
it retains the HEAR as a publicly-downloadable electronic document. The
graduate is issued with the URL for downloading their HEAR, which they
can pass onto employers or other relying parties. The replying party can
use the URL to download the HEAR for an applicant, and verify the
document signature as before.

Note that this model does not also preclude the Type 1 model, as the
graduate themselves may choose to download and directly distribute the
document.

![Public Online Document Model diagram](hear_type2.png){width="543"
height="578"}

### Type 3: Ticket Release Model

In this model the HEAR electronic document is created and signed by the
issuing institution, and maintained within a protected repository. The
graduate is issued with the URL for accessing their HEAR, which also has
a parameter containing a unique ticket that grants access to the
document. As in the Type 2 scenario, the graduate can pass on the URL
and ticket to a relying party to enable them to access, download, and
verify the HEAR. The difference in this scenario is that without a valid
ticket, each of which is keyed to a specific HEAR document, access to
HEAR documents is denied.

![Ticket Release Model diagram](hear_type3.png){width="547"
height="578"}

Note that the URL and access ticket may in fact take the form of a
standard link containing a parameter, e.g.:

> https://www.easthampton.ac.uk/hear/1234567890?ticket=12321abc234234efff324234223abcd

It requires no special software or configuration to be used by the
relying party to make use of this architecture.

### Type 4: Limited-Use Ticket Release Model

In this model the HEAR electronic document is created and signed by the
issuing institution, and maintained within a protected repository. The
graduate is issued with credentials (typically a username and password)
for accessing an extranet at the issuing institution (or outsourced
service provider). When the graduate wishes to grant access to their
HEAR to an employer or other relying party, they must login to the
extranet with their credentials, and generate a new ticket that will
grant limited access. The ticket and URL are sent to the relying party
(or the graduate can copy this information into an email they send
themselves), and the relying party can then use the ticket to access,
download, and verify the HEAR.

After downloading, the ticket may be revoked by the service to prevent
its further use; similarly, a ticket may be issued with a use-by date
and be automatically revoked when this has expired. Also, users may be
able to control access to a document independently of any
ticket-specific mechanisms; this is discussed further in the section on
security considerations.

Depending on requirements the relying party may need to register and
login to make use of the service, in addition to possessing a valid
ticket.

![Limited-Use Ticket Release Model diagram](hear_type4.png){width="558"
height="577"}

### Type 5: Document Share Model

In this model the HEAR electronic document is created and signed by the
issuing institution, and maintained within a protected repository. The
graduate is issued with credentials (typically a username and password)
for accessing an extranet at the issuing institution (or outsourced
service provider). When the graduate wishes to grant access to their
HEAR to an employer or other relying party, they must login to the
extranet with their credentials, and generate a new ticket that will
grant limited access to the extranet for the relying party. The ticket
and URL are sent to the relying party (or the graduate can copy this
information into an email they send themselves), and the relying party
can then use the ticket to access online (but not download) the HEAR.
After accessing the extranet, the ticket may be revoked by the service
to prevent its further use; similarly, a ticket may be issued with a
use-by date and be automatically revoked when this has expired.

Depending on requirements the relying party may need to register and
login to make use of the service, in addition to possessing a valid
ticket.

The primary difference between Type 4 and Type 5 systems is that the
Type 5 system does not share any physical documents, but instead offers
online access rather like Google Docs.

![Document Share Model diagram](hear_type5.png){width="570"
height="515"}

### Multiple models

It is entirely appropriate to offer multiple models of access and
verification, for example both Type 1 and Type 2, or Type 5 and Type 1,
particularly where the HEAR itself comprises multiple digital artefacts
with different requirements for access and verification. This is
discussed further in the section below on composite access and
verification requirements.

\

Privacy and Security Considerations
-----------------------------------

The nature of verification and access control depends on several key
decisions that institutions make:

1.  What the HEAR record contains. If this includes sensitive personal
    information in addition to public statements, then this will require
    access management.
2.  The business model that underpins the use of the HEAR. For example,
    whether the issuing institution engages in a partnership with
    recruitment agencies, or has a fee charging model for verification.

The questions of the content of the records and the nature of the
business model should be explored by projects and determined by issuing
institutions; it is not determined by the technical architecture, but
has a very important impact on the choices available.

#### Signing and Verifying HEAR documents

For the electronic HEAR to have long-term legal validity and be capable
of being verified, it must:

1.  use an electronic signature conforming to a recognised standard
2.  use a recognised standard timestamp, ensuring that the document was
    signed at a particular date and time
3.  be able to be periodically re-stamped (notarised) to ensure
    long-term validity

We recommend that implementations conform to the European
Telecommunications Standards Institute (ETSI) standards for Advanced
Electronic Signatures. These standards build upon the W3C XML Digital
Signatures specification, and are recognised under European Union
Directive 1999/93/EC.

#### Tamperproofing

If an electronic hear is signed using a digital signature, then the
resulting document is tamper-evident; that is, if any amendments are
made to the document after it is signed, then this will be evident when
evaluating the signature. Electronic signatures conforming to the AES
standards, as discussed in the previous section, have this capability.

#### Access Control

If the HEAR needs access control, this can be for reasons of privacy or
for business purposes. In either case, there is always a tradeoff to be
made between the degree and cost of security, and the value of the
target. If the value of the target can be reduced (for example,
referencing other more secure information rather than replicating it in
the document) then the degree and cost of security can be reduced.
However, if the HEAR includes replicated sensitive personal information
this increases the document value and requires more costly security
procedures.

If access control by the subject is required, the issues are then raised
of how credentials are issued, and how individuals are verified. Account
management can be a significant cost, for example supporting retrieving
lost credentials, account revocation, and monitoring suspicious access
patterns. However, individual access control also enables individuals to
control access to their information in more sophisticated and convenient
ways; for example, closing down access to all their documents t third
parties after accepting a job offer.

Again, this is a topic that needs consideration by implementers from a
business as well as a technical point of view.

#### Composite privacy, verification and access requirements

The complete set of achievement information for any graduate spans
multiple levels of privacy and sensitivity. For implementers this raises
the question of how to address these different levels of concern in the
system architecture.

One approach is to divide the parts of the achievement information into
separate electronic documents, each of which can be handled by a
mechanism that implements an appropriate access and verification
mechanism; for example, the diploma on its own may be a publicly
downloadable document using a simple Type 1 architecture, whereas the
transcript uses a Type 5 architecture, and additional personal
information uses Type 5 access control but without a verification stamp.
This is the simplest to implement, and requires only that each part can
be addressible in terms of policy (e.g. separately identifiable diploma
and transcript objects rather than a single monolithic report).

A more complex approach is to use a *policy-combining algorithm* to
determine access based on the parts being requested. This requires that
not only are parts identified, but also that the policies governing the
parts can be expressed using a standard language, and combined within a
single policy decision and enforcement system. The XACML specification
is designed with this in mind, but is a very complex system to implement
and may be beyond the capabilities of many issuing institutions to
manage and maintain.

#### Safeguarding tickets from eavesdropping and replay attacks

If tickets are sent to the repository over a standard HTTP connection
there is always the possibility that the traffic can be intercepted and
the request replayed at a later date by a third party. To prevent this
the repository implementation may:

1.  Issue single-use tickets under the Type 4/5 scenario
2.  Only conduct transactions using TLS encryption (HTTPS)
3.  Both of the above

#### Falsifying providers

It is entirely feasible for an individual to setup a fake university
website implementing the architecture described in this document, and
then sign their own made-up HEAR electronic documents to distribute to
other parties. The only protection against this is to inspect the
issuing authority of the HEAR and verify it as a trusted education
provider. A simple mechanism is to check the web address – for example,
that the HEAR is coming from

> https://www.easthampton.ac.uk

and not something along the lines of:

> http://www.easthampton-ac-uk.com/

Another approach is to make use of a trusted source of institutional
information, such as the UK Register of Learning Providers
(<http://www.ukrlp.co.uk/>). If a HEAR document contains a UK Provider
Reference Number (UKPRN) then this can be cross-checked to ensure that
the document is signed using a key from the registered internet domain
of that provider and not from another source, or in a Type 5
architecture that the extranet the relying party is visiting matches the
entry in the UK RLP.

Finally, if the mechanism for sharing the URL for accessing the HEAR is
under the control of the Institution, then they may use a digitally
signed email, which can be used to verify that the URL was sent from an
authorised address.

In all these cases the issuing institution MUST manage its TLS signing
keys effectively.

#### Avoiding Guessable tickets

Implementations using a Type 3/4/5 architecture should ensure that they
act to prevent other parties guessing a correct URL-ticket combination.
Implementation may use one or more of the following strategies:

1.  Monitor traffic and shut out IP addresses that appear to be
    attempting brute-force cracking of the system
2.  When generating tickets include a nonce value generated using a
    high-quality random number algorithm
3.  Use an appropriate ticket length to increase the search space that a
    party would need to attack

#### Stolen Tickets

It is possible that under a Type 3/4/5 architecture that a graduate may
have their ticket stolen in some fashion; for example, leaving it on a
USB drive, accidentally disclosing it online, etc. In such cases
implementations may want to restrict the extent to which stolen tickets
can be used to access documents. A number of strategies can be
considered:

1.  Under a Type 4/5 system, the identity of the relying party may be
    encoded in the ticket itself, so that the repository can check
    whether the request originates in the same domain as the ticket.
2.  If a graduate suspects they have lost or disclosed their ticket, the
    system may provide a means of for them to request revocation of
    the ticket. This is particularly relevant in a Type 2 architecture,
    where use of a single ticket is unlimited.
3.  Tickets under a Type 4/5 system may be time-limited and expire
    automatically, reducing the window of opportunity for using a
    stolen ticket.

#### Auditing

Implementations using a Type 3/4/5 architecture should as a matter of
best practice record the use of tickets to access HEAR documents for
auditing purposes. Tickets that are revoked or expired, and the access
logs based on those tickets, should also be retained for auditing.

Deployment Considerations
-------------------------

Depending on the cost and complexity of the solution required, issuing
institutions may wish to consider external hosting arrangements with
specialist service providers, or to combine with other issuing
institutions to share a common solution (i.e., a shared service). There
is no reason in principle not to do this; the key issues to be
considered in such cases are the governance, cost, business case, and
legal implications.

For example, the models described above can apply to:

-   A single institution using a locally hosted and managed repository
    and service portal
-   A federation of institutions (such as GMSA, SURF or a LLN) sharing a
    single repository and portal
-   A federation of institutions sharing a single portal and access
    solution, but individual repositories
-   A national shared repository and portal service

Other implementation guidance
-----------------------------

### Protocols

The core document access service, and especially the document access
URLs and tickets, should be developed using the standard web protocols,
HTTP and HTTPS (HTTP with Transport Layer Security, TLS).

Additional protocol layers, such as SOAP/WSDL are not recommended for
the outward-facing services as they increase implementation costs and
minimum technical requirements for both the issuing institution and
relying parties.

However, a solution may use Service-Oriented Architecture and more
complex specifications in its implementation, typically for
internally-facing services.

### Identifiers & URLs

Where URLs or identifiers are used in any part of the HEAR, these should
be issued and maintained with a policy of long-term management. Once a
URL or identifier is encoded in a HEAR then that URL is being stamped
and verified by the institution as a valid identifier or reference; this
means that institutions MUST maintain those URLs for the lifetime of the
HEAR, and in particular identifiers and URLs MUST NOT be reallocated to
other resources.

### Partial versus whole records

It may be useful for implementers to offer services (web APIs) that
expose partial rather than complete HEAR records, execute queries, or
aggregate reports from multiple HEARs. This can form a value-added
service for partner organisations, for example.

In general such services should be designed with the same security and
privacy considerations as complete HEAR records; wherever possible
sensitive information should not be shared using such services, unless
the issuing institution is willing and capable of implementing the
necessary systems, policies and procedures.
