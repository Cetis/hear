---
layout: default
---

HEAR 1.0 Specification 
======================



About
===============================================================================================================================================================================================
Status

This is currently a working draft of version 1.0.


Patents

This specification is subject to a royalty free patent policy.

There are no known patents covering any of this work. If you think that
part of this work may be subject to an existing or pending patent,
please email the editors.


### Copyright and License

TBC


### Inspiration and acknowledgements


Introduction
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


Conformance
===========================================================================================================================================================================================================



There are two classes of application that can conform to this
specification:

-   A *producer* is a class of application that produces HEAR XML
    documents
-   An *consumer* is a class of application that consumers HEAR XML
    documents

A product MAY belong to both classes.

A **strictly conforming instance** is a set of structured information
constituted only of elements and attributes defined by this
specification and *fully qualified refinements* of the elements defined
in this specification.

A **fully qualified refinement** is defined for the purpose of
conformance as an element that explicitly extends an element defined by
this specification. A fully qualified refinement must be capable of
being processed according to the semantics of the element it extends.

A **conforming instance** MAY contain additional elements and attributes
not defined by this specification.

A **conforming producer** MUST be capable of generating and sharing
*strictly conforming instances*.

A **conforming consumer** MUST be capable of processing *strictly
conforming instances*.


HEAR Documents
=================================================================================================================================================================================================================

A producer MUST create HEAR documents that are valid XML documents.

A producer MUST create HEAR documents with one of the following elements
as its top-level element:

-   AchievementReport

A consumer MUST be able to process a valid HEAR XML document.

The HEAR Template
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

*This section is non-normative*

This specification covers the structure of the XML representation of the
HEAR data; it does not define the structure of the HEAR document per se.
The following information is provided to give context to the
specification of the data elements. Readers are asked to refer to the
[HEAR Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf "http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf"){.external
.text} for more details.

A HEAR must adhere to the prescribed template described in the [HEAR
Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf "http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf") The Guidance defines the sections of the HEAR and requires that
sections are numbered and follow the sequence and explanatory guidance
given in the Guidance Document.

The structure of the template for a HEAR is as follows:

-   Contextual information
-   Section 1. Information identifying the holder of the qualification
-   Section 2. Information identifying the qualification
-   Section 3. Information on the level of the qualification
-   Section 4. Information on the contents and results gained
-   Section 5. Information on the function of the qualification
-   Section 6. Additional information
-   Section 7. Certification of the HEAR
-   Section 8. Information on the national higher education system

On output for printing or for viewing electronically a HEAR should
contain section numbering and standard statements as described in the
[HEAR Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf "http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf")


### Contextual Information

The [HEAR Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf "http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf"){.external
.text} gives details of statements that should be included in the HEAR
at specified points, for example a standard statement at the start of
the HEAR should be included in order to meet the requirements of the
European Diploma Supplement (DS). Information about these statements is
included in the Guidance sections of this specification.




Guidelines In the Contextual Information of the HEAR,
institutions SHOULD include the following statements:

*This Higher Education Achievement Report follows the model developed by
the European Commission, Council of Europe and UNESCO/CEPES for the
Diploma Supplement.*

*The purpose of the Supplement is to provide sufficient recognition of
qualifications (diplomas, degrees, certificates etc). It is designed to
provide a description of the nature, level, context and status of the
studies that were pursued and successfully completed by the individual
named on the original qualifications to which this Supplement is
appended. It should be free from any value judgements, equivalence
statements or suggestions about recognition. Information in all eight
sections should be provided. Where information is not provided, an
explanation should give the reason why.*


XML Document Structure
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This section describes diagrammatically the main information elements of
the HEAR XML document structure and their relationships. Definitions are
included under the Core Elements section.

The HEAR model includes information drawn from Student Records Systems,
Course Information Systems and supporting systems that will be created
and maintained by various different administrative processes and
academic practices within academic institutions. The model builds upon
information about learners, descriptions of programmes and other
learning opportunity structures, information about modules and other
educational components enrolled on by learners, assessment results and
other accredited achievements for each completed learning opportunity,
and information about the awarding and providing organisations
themselves.

[![Image:HEAROutlineInformationModel2011-02-17.png](images/HEAROutlineInformationModel2011-02-17.png)]

Core elements
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


###  The &lt;achievementReport&gt; element

*URI: \[to be completed\]*


#### Definition

The default root element for a HEAR.


#### Core elements used within the achievementReport element

-   issuer (required, one only)
-   learner (required, one only)
-   awardedBy (required if different from issuer, one only)
-   qualification (required, one only)
-   provider (required, one or more)
-   course(s) (required, at least one)
-   assessment (required, at least one per presentation)
-   certificationOfTheHEAR (required, one only)
-   additionalInformation (optional, one only)


Guidelines These core elements are listed here, so that the major
components of a HEAR are clearly indicated. Some of these elements are
sub-elements of top level elements, as noted in this guidance.

**awardedBy:** A component of qualification (see
[XCRI-CAP](Qualification "http://www.xcri.org/Qualification"){.external
.text} specification).

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-73710929-1', 'auto');
  ga('send', 'pageview');

</script>

**qualification:** A component of course (see
[XCRI-CAP](Course "http://www.xcri.org/Course"){.external
.text} specification).

**course:** A component of provider (see
[XCRI-CAP](Course "http://www.xcri.org/Course"){.external
.text} specification).

**assessment:** A component of presentation (see
[XCRI-CAP](Presentation "http://www.xcri.org/Presentation"){.external
.text} specification)

**Absence of provider:** Where a provider is not specified, consumers
SHOULD interpret this as meaning that the awardingBody is also the
provider.

 Specification of elements below the root element
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


###  element


#### Definition

The organisation that is responsible for producing the HEAR.


#### Constraints

A valid HEAR MUST contain one and only one issuer instance.

An issuer instance MUST contain the sub-elements defined below and no
other elements.


####  Namespaces

Uses namespace dc: 

Uses namespace dcterms: 


#### 

-   identifier, dc\#identifier (required, multiple)
-   title, dc\#title (required, multiple)


Guidelines This element identifiers the issuing organisation,
which may be a different organisation from the provider or the awarding
body, for example a broker.

The &lt;issuer&gt; element MUST NOT contain any other elements. Further
elements describing the organisation(s) offering the course or awarding
the qualification MUST be contained in the provider element.


###  the &lt;learner&gt; element


####  Definition

Information identifying the holder of the qualification.


#### Constraints

A valid HEAR MUST contain one and only one learner instance.

A learner instance MUST contain the sub-elements defined below and no
other elements.


#### Namespaces

Uses namespace elm: European Learner Mobility Achievement Information
(EuroLMAI).

Uses scop: the SEMIC-EU Core Person Specification (not yet published in
machine readable form), which is compatible with EuroLMAI.

Uses namespace dc: 

Uses namespace dcterms: 




Note The elm namespace relates to the European Learner Mobility
Achievement Information (EuroLMAI), for which see [CWA
16132](http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf "http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf") The elements in hear:learner are fully compatible and strictly
compliant with the elm:Learner profile, which specifies vCard properties
for these elements, including Identifier. These are UK-specific
implementations.




#### Sub-elements used in the &lt;learner&gt; element

-   **[identifier](Identifier_(HEAR) "Identifier (HEAR)")** (required,
    at least one), dc\#identifier. Unique identifier for the learner.
-   **familyName** (required, one element only), elm\#familyName. Full
    family or surname, as included on official documents, such as
    a passport.
-   **givenNames** (required, one element only), elm\#givenNames. All
    given or first names in the order specified by the learner, as
    included on official documents, such as a passport.
-   **fullName** (required, one only), elm\#fullName. The complete name
    of the learner; components should be those included on official
    documents, such as a passport.
-   **birthday** (required, one only), scop\#dateOfBirth. Date of birth
    of the learner.



-   **identifierDescription** (optional), used to indicate the
    provenance of the identifier. Required text for the HUSID is as
    follows

"HUSID (HESA Unique Student Identifier) is the unique national
identifying number for students registered at a UK university. It is
defined by HESA, the UK's Higher Education Statistics Agency."




Guidelines **dateOfBirth**: This value MUST be in ISO 8601 date
format, yyyy-mm-dd (example: "1985-05-16"). Note that this specification
does not prescribe the final form output for date (for example in a PDF
or paper document); implementers may wish to present the date in an
alternative format to end users. Additionally there may be applications,
such as outputs for employers, in which the inclusion of the learner's
dateOfBirth is not required.

**identifier**: Where the HESA Unique Student Identifier (HUSID) is
known, for example stored in the Student Record System, this value MUST
be the learner's HUSID. In other cases a different authoritative
identifier MUST be used. Alternatives recommended in this specification
include the Unique Learner Number (ULN) and the Scottish Candidate
Number (SCN). Namespace refinements for these identifiers are included
in the HEAR XML schema. For identifiers other than the HUSID, ULN or SCN
implementers MUST either extend the identifier element to include
another namespace or indicate the provenance of the identifier in the
comment attribute. An internal issuer or awardingBody identifier can
also be included.




### the &lt;qualification&gt; element

*URI: *


#### Definition

A status awarded to or conferred on a learner by an awarding body.


#### Constraints

A valid HEAR MUST contain one and only one qualification instance.
Instances of associate qualifications or other achievements not forming
part of the learner's academic achievements as a result of following the
indicated programme of study MAY be recorded in the Additional
Information element.

A qualification instance MUST contain the required sub-elements defined
below and MAY contain the optional sub-elements.

Producers MUST ensure that the qualification element of the HEAR relates
directly to the top level course element in a one-to-one relationship.
Each HEAR contains information about one and only one qualification,
achieved by a learner as a result of completion of one and only one top
level course.


#### Namespaces

Uses namespace qm: , refined in XCRI-CAP 1.2,
for which see
[http://www.xcri.org/XCRI\_1.2\_Qualifications](XCRI_1.2_Qualifications "http://www.xcri.org/XCRI_1.2_Qualifications"){.external
.free}

Uses namespace xcri:  and xcriTerms:


Uses namespace elm: European Learner Mobility Achievement Information
(EuroLMAI), for which see [CWA
16132](http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf "http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf")

Uses namespace eds: [European Diploma
Supplement](http://europass.cedefop.europa.eu/europass/home/vernav/InformationOn/EuropassDiplomaSupplement.csp "http://europass.cedefop.europa.eu/europass/home/vernav/InformationOn/EuropassDiplomaSupplement.csp"){.external
.text}

Uses namespace dc: 

Uses namespace dcterms: 




Note XCRI refers to the [eXchanging Course Related Information -
Course Advertising Profile (XCRI-CAP v1.1) eProspectus
standard](http://www.xcri.org/wiki/ "http://www.xcri.org/wiki/")

There are currently no elements declared within the namespaces qm, elm,
eds.

\




#### Sub-elements used in the &lt;qualification&gt; element

-   identifier (required, one only), dc\#identifier. Unique identifier
    for the qualification.
-   title (required, one only), dc\#title. Full official name of
    the award.
-   [description](HEAR_Description "HEAR Description") (required, one or
    more), xcri\#description. Further descriptive text about the
    qualification (see Guidelines).
-   subject (required, at least one), dc\#subject. Main field(s) of
    study for the qualification.
-   level (required, one only), hear\#level. Numerical position of the
    qualification in the relevant national qualifications framework.
-   qualificationHolderTitle (optional, zero or
    one), eds\#qualificationHolderTitle. Nationally accepted title
    conferred by the award, for example *Bachelor of Science (Honours)*.
-   issueDate (required, one only), elm\#issueDate. Date on which the
    qualification was awarded.
-   awardedBy (required, one only), qm\#awardedBy. This element
    identifies and names the recognised organisation (Awarding Body)
    that confers the qualification upon the learner.




Guidelines **description:** Use the recommended encoding scheme
to provide detailed information about the qualification in different
information categories. See the encoding scheme for more details.

**subject:** Put each main field of study in a separate element. On
output, the elements should be concatenated to form one string. There is
no nationally approved vocabulary for the subject in a HEAR. Use the
institution's own terminology. If subjects or fields of study are not
held in respect of qualifications, use the subjects in respect of the
top level course (programme) element.

**level:** The level element MUST contain both the numerical position of
the qualification in the relevant national qualifications framework and
a cross-reference to section 8: Information on the national Higher
Education System. See guidance on Education Levels and Frameworks at
[http://www.xcri.org/XCRI\_1.2\_Qualifications](XCRI_1.2_Qualifications "http://www.xcri.org/XCRI_1.2_Qualifications"){.external
.free}.

**awardedBy:** The element content SHOULD contain the official name of
the Awarding Body.




#### Attributes

-   id, attribute of awardedBy.


Guidelines **id:** The id attribute MUST identify the Awarding
Body specified in the awardedBy element. It MUST be A Uniform Resource
Identifier (URI) conforming to the URL scheme as specified by [IETF RFC
3986](http://tools.ietf.org/html/rfc3986 "http://tools.ietf.org/html/rfc3986")




### the &lt;provider&gt; element

*URI: *


#### Definition

An organisation that offers one or more courses.


#### Constraints

A valid HEAR MUST contain one or more provider instances.

A &lt;[description](HEAR_Description "HEAR Description")&gt; element
MUST contain a statement about the status of the institution where the
programme of study was undertaken (see Guidance Document section 2).

A provider instance MUST contain the required sub-elements defined
below.

Producers MUST ensure that provider instances contain information only
about providers of courses undertaken by the learner in the context of
the qualification awarded.


#### Namespaces

Uses namespace xcri: 




Note XCRI refers to the [eXchanging Course Related Information -
Course Advertising Profile (XCRI-CAP v1.1) eProspectus
standard](http://www.xcri.org/wiki/ "http://www.xcri.org/wiki/")




#### Sub-elements used in the &lt;provider&gt; element

-   identifier (required, at least one), xcri\#identifier. Unique
    identifier for the provider.
-   title (required, at least one), xcri\#title. Full official name of
    the provider.
-   [description](HEAR_Description "HEAR Description") (required, at
    least one), xcri\#description. Details of the status of the provider
    and any further relevant details, including any statement about the
    relationship between the provider and the awarding body, if these
    are different organisations.
-   course (required, at least one), hear\#course. Details of
    the course(s) through which the learner achieved the award of
    the qualification.

Examples:

         http://www.universityoftest.ac.uk/
         12345678
         1234


### the &lt;course&gt; element

*URI: *


#### Definition

A course provides details of a learning opportunity offered by a
learning provider.


#### Constraints

A valid HEAR MUST contain one and only one top level course element.
Further course elements MAY be included to reflect the institution's
programme component structures.

The top level course element SHOULD define the Programme Level learning
opportunity undertaken by the learner.

Producers MUST ensure that the top level course element of the HEAR
relates directly to the qualification element in a one-to-one
relationship. Each HEAR contains information about one and only one
qualification, achieved by a learner as a result of completion of one
and only one top level course.

Course elements at levels lower than programme level SHOULD be related
to the top level course element using the relation&gt;isPartOf element,
either directly through inclusion of the identifier of the top level
course, or indirectly through inclusion of the identifier of another
course element.

Example

        
            
            1234
            Information and Communications Undergraduate Programme
        
        
            
            1234-01
            Digital Media and Communications - Stage 1
            1234
        
        
            
            M223
            Information Literacies for the Digital Age
            1234-01
        


#### Namespaces

Uses namespace xcri:  and
xcriTerms: 


#### Sub-elements used in the &lt;course&gt; element at Programme Level

-   identifier (required, one only), xcri\#identifier.



-   title (required, one only), xcri\#title. Full official name of
    the programme.



-   [description](HEAR_Description "HEAR Description") (required, one or
    more), xcri\#description. Further descriptive text about the
    qualification (see Guidelines).



-   credit (optional, multiple), xcri\#credit. Details of the credit
    values and levels earned on successful completion of the programme.




Guidelines **description**: Use the recommended encoding scheme
to provide detailed information about the qualification in different
information categories. See the encoding scheme for more details.




#### Attributes

-   courseType (optional). Identifies whether the course is at programme
    level, year, stage or module. Producers MAY use an encoding scheme
    or controlled vocabulary for this item.


#### Sub-elements used in the &lt;course&gt; element at other levels 

-   identifier (required, one only), xcri\#identifier.



-   title (required, one only), xcri\#title. Full official name of the
    module or other component.



-   credit (optional, one only), xcri\#credit. Details of the credit
    values and levels earned on successful completion of the modules
    or components.



-   type (required, one only), mlo\#type
    (mlo:LearningOpportunitySpecification, type). Indicates the type of
    component, such as a module-level component or a grouping component
    such as semester, programme year, level or subject of a programme.



-   relation (required, one only), xcri\#relation. Indicates the parent
    course element, using isPartOf attribute.


#### Sub-elements used in the &lt;presentation&gt; element at Programme Level

-   identifier (required, one only), xcri\#identifier.



-   start (required, one only), xcri\#start. The date at which the
    programme begins. See \[EN 15982\].



-   end (required, one only), xcri\#end. The date at which the
    programme ends.



-   [description](HEAR_Description "HEAR Description") (required, one or
    more), xcri\#description. Further descriptive text about the
    qualification (see Guidelines).



-   duration (required, one only), xcri\#duration. The length of
    the programme.



-   studyMode (required, one only), xcri\#engagement (studyMode). A
    general expression of the overall amount of the student's time that
    is devoted to the learning opportunity, as defined by the provider.



-   languageOfInstruction (required, at least
    one), xcri\#languageOfInstruction. A language in which the
    presentation was taught.



-   languageOfAssessment (required, at least
    one), xcri\#languageOfAssessment. A language in which the
    presentation was assessed.



-   assessment (optional). Information about the assessment of
    the presentation.




Guidelines **identifier:** Where presentation does not have its
own identifier, producers SHOULD use and repeat the host course
identifier.

**title:** Producers SHOULD draw the title from the course element, not
the presentation element.

**start**: This is a *temporal element*. For more information on the
syntax of this element, see the section on temporal elements.

**end:** This is a *temporal element*. For more information on the
syntax of this element, see the section on temporal elements.

**description**: Use the recommended encoding scheme to provide detailed
information about the qualification in different information categories.
See the encoding scheme for more details.

**duration:** The content of this element MUST be human readable text of
the form 'value' followed by 'unit of time', for example 'Three years'.
The duration SHOULD be expressed in years, unless the course is shorter
than two years, in which case an expression in months or weeks is
acceptable. Producers MAY include a machine-readable attribute
'interval' that follows the ISO 8601 standard.

Example

        Three years

**studyMode:** See
[http://www.xcri.org/XCRI\_Terms\_1.2\#studyMode](XCRI_Terms_1.2#studyMode "http://www.xcri.org/XCRI_Terms_1.2#studyMode"){.external
.free}

**languageOfInstruction:** The content of this element MUST be a valid
[BCP-47 language
tag](http://tools.ietf.org/rfc/bcp/bcp47.txt "http://tools.ietf.org/rfc/bcp/bcp47.txt") Default value: EN.

**languageOfAssessment:** The content of this element MUST be a valid
[BCP-47 language
tag](http://tools.ietf.org/rfc/bcp/bcp47.txt "http://tools.ietf.org/rfc/bcp/bcp47.txt") Default value: EN.

**assessment :** In an exit HEAR this element MUST be present for each
presentation, otherwise it is optional.

**Output of languageOfInstruction and languageOfAssessment:** Consumers
SHOULD present final form output of these elements as human readable
text.

**Absence of languageOfInstruction and languageOfAssessment:** Where
these elements are missing, consumers SHOULD interpret this as meaning
that the language of instruction and assessment was English (en-GB).

\




#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0_Specification&action=edit&section=46 "Edit section: Sub-elements used in the &lt;presentation&gt; element at other levels")\]  Sub-elements used in the &lt;presentation&gt; element at other levels

-   identifier (required, one only), xcri\#identifier.



-   assessment (optional). Information about the assessment of
    the presentation.


### the &lt;assessment&gt; element


#### Definition

The details of the way in which the learner's performance in the
presentation was judged.


#### Constraints

A valid exit HEAR must contain an &lt;assessment&gt; element for the
programme and for each module or course component that is part of the
programme or that is an additional academic credit-bearing student
achievement detailed in the HEAR.

Each &lt;assessment&gt; element must relate only to the learner and the
specific version of the presentation on which the learner was assessed.

NOTE: decision on retakes and numbers of attempts is still outstanding -
[Alan Paull](Alan_Paull "Alan Paull")


#### Namespaces

Uses namespace xcri: .

Uses namespace elm: European Learner Mobility Achievement Information
(EuroLMAI), for which see [CWA
16132](http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf "http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf")

Uses namespace eds: [European Diploma
Supplement](http://europass.cedefop.europa.eu/europass/home/vernav/InformationOn/EuropassDiplomaSupplement.csp "http://europass.cedefop.europa.eu/europass/home/vernav/InformationOn/EuropassDiplomaSupplement.csp"){.external
.text}




Note XCRI refers to the [eXchanging Course Related Information -
Course Advertising Profile (XCRI-CAP v1.1) eProspectus
standard](http://www.xcri.org/wiki/ "http://www.xcri.org/wiki/")




#### Sub-elements used in the &lt;assessment&gt; element

-   identifier (required, one only). Unique identifier for the
    &lt;assessment&gt; element.



-   assessmentType (required, one only). Description of the style of
    the assessment.



-   assessmentWeight (optional, zero or one). Weighting of the
    assessment result as a proportion of the overall assessment for
    the presentation.



-   attempts (optional, zero or one). Number of times the learner has
    made at the assessment.



-   result (optional, multiple), elm\#result. The actual outcome of a
    presentation for a learner as stated by a provider or issuer.



-   [description](HEAR_Description "HEAR Description") (required, one or
    more), xcri\#description. Details of the grading scheme used by
    the assessment. This element matches with the
    elm:gradingScheme entity.




Guidelines **assessmentType:** It is recommended that producers
use an encoding scheme or controlled vocabulary for this item.

**result:** Required in an exit HEAR, one only per assessment.

**[description](HEAR_Description "HEAR Description"):** Use the
recommended encoding scheme to provide detailed information about the
assessment in different information categories. See the encoding scheme
for more details.




#### Attributes

-   resultType: used with **result**. Indicates whether the result is a
    mark, grade or similar. It is recommended that producers use an
    encoding scheme or controlled vocabulary for this item.


### the &lt;additionalInformation&gt; element

*URI: This will relate to elm:additionalInformation; URI not yet
available.*


#### Definition

Details of the richer picture of verified student achievement, including
additional awards (with or without academic credit), additional
recognised activities, and university, professional and departmental
prizes.


#### Constraints

A valid HEAR MUST contain one and only one additionalInformation
element. Guidance on its contents is given in the 'Guidance to Inform
Institutional Implementation'


#### Namespaces

Uses namespace elm: European Learner Mobility Achievement Information
(EuroLMAI), for which see CWA 16132.


#### Sub-elements used in the &lt;additionalInformation&gt; element

-   [description](HEAR_Description "HEAR Description") (required, one or
    more), xcri\#description. Further descriptive text about the
    learner's achievements outside the qualification. See guidelines.



-   ePortfolioUrl (optional, zero or one), xcri\#url. A hypertext link
    to the learner's ePortfolio.

\




Guidelines **description:** Use the recommended encoding scheme
to provide detailed information about the achievements in different
information categories. See the encoding scheme for more details.




### the &lt;certificationOftheHEAR&gt; element


#### Definition

Provides evidence that the HEAR is a genuine document produced by the
authorised organisation.


#### Constraints

A valid HEAR must contain one and only one
&lt;certificationOftheHEAR&gt; element.


#### Sub-elements used in the &lt;certificationOftheHEAR&gt; element

-   identifier (required, one only), dc\#identifier. Uniquely identifies
    this version of the HEAR data set for this learner.



-   date (required, one only). Date and time of the production of
    this HEAR.



-   fullName (required, one only). Full name of the official certifying
    the HEAR.



-   capacity (required, one only). The official post of the
    certifying individual.



-   signature (required, one only). 