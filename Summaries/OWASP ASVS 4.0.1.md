*ME: ASVS is a the "must-to-read" for all software developers.*  

https://github.com/OWASP/ASVS/tree/v4.0.1  

FIDO, Yubico YubiKey, etc: https://www.youtube.com/watch?v=TJP9fCsDLCI  
https://www.youtube.com/watch?v=MHTIVR1mY7k  

The NIST 800 Series is a set of documents that describe United States federal government computer security policies, procedures and guidelines. NIST (National Institute of Standards and Technology) is a unit of the Commerce Department.  

What's new in 4.0  
The most significant change in this version is the adoption of the NIST 800-63-3 Digital Identity Guidelines, ...  

The OWASP Top 10 2017 and now  
the OWASP Application Security Verification Standard have now aligned with NIST 800-63 for authentication
and session management. We encourage other standards-setting bodies to work with us, NIST, and others to
come to a generally accepted set of application security controls to maximize security and minimize
compliance costs.  

New in 4.0 is a comprehensive mapping to the Common Weakness Enumeration (CWE), one of the most
commonly desired feature requests we've had over the last decade. CWE mapping allows tool manufacturers
and those using vulnerability management software to match up results from other tools and previous ASVS
versions to 4.0 and later.  

Not every item in the
ASVS has an associated CWE, and as CWE has a great deal of duplication, we've attempted to use the most
commonly used rather than necessarily the closest match.  

We have worked to comprehensively meet and exceed the requirements for addressing the OWASP Top 10
2017 and the OWASP Proactive Controls 2018. As the OWASP Top 10 2017 is the bare minimum to avoid
negligence, we have deliberately made all but specific logging Top 10 requirements Level 1 controls, making it
easier for OWASP Top 10 adopters to step up to an actual security standard.  

https://www.pcisecuritystandards.org/pci_security/  

Lastly, we have de-duped and retired less impactful controls. Over time, the ASVS started being a
comprehensive set of controls, but not all controls are equal at producing secure software. This effort to
eliminate low impact items could go further. In a future edition of the ASVS, the Common Weakness Scoring
System (CWSS) will help prioritize further those controls which are truly important and those that should be
retired.  

As of version 4.0, the ASVS will focus solely on being the leading web apps and service standard, covering
traditional and modern application architecture, and agile security practices and DevSecOps culture.  
  
  
System / people  

Level 1 is the only level that is completely penetration testable using humans. All others require access to
documentation, source code, configuration, and the people involved in the development process. However,
even if L1 allows "black box" (no documentation and no source) testing to occur, it is not an effective
assurance activity and should be actively discouraged.  
...  
Black box testing, often performed at the end of development, quickly, or not at all, is completely
unable to cope with that asymmetry.  

One of the best ways to use the Application Security Verification Standard is to use it as a blueprint to create a
Secure Coding Checklist specific to your application, platform or organization. Tailoring the ASVS to your use
cases will increase the focus on the security requirements that are most important to your projects and
environments.  

Verify that all high-value business logic flows, including authentication, session management and access
control are thread safe and resistant to time-of-check and time-of-use race conditions.  

The identifiers may change between versions of the standard therefore it is preferable that other documents,
reports, or tools use the format: v<version>-<chapter>.<section>.<requirement>, where: 'version' is the ASVS
version tag. For example: v4.0.2-1.11.3  

If identifiers are used without including the v<version> element then they should be assumed to refer to the
latest Application Security Verification Standard content. Obviously as the standard grows and changes this
becomes problematic, which is why writers or developers should include the version element.  

It is not possible to fully complete ASVS verification using automated penetration testing tools alone. Whilst a
large majority of requirements in L1 can be performed using automated tests, the overall majority of
requirements are not amenable to automated penetration testing. 
Please note that the lines between automated and manual testing have blurred as the application security
industry matures. Automated tools are often manually tuned by experts and manual testers often leverage a
wide variety of automated tools.  

In version 4.0, we decided to make L1 completely penetration testable without access to source code,
documentation, or developers. Two logging items, which are required to comply with OWASP Top 10 2017
A10, will require interviews, screenshots or other evidence collection, just as they do in the OWASP Top 10
2017. However, testing without access to necessary information is not an ideal method of security verification,
as it misses out on the possibility of reviewing the source, identifying threats and missing controls, and
performing a far more thorough test in a shorter timeframe.  

Where possible, access to developers, documentation, code, and access to a test application with non-
production data, is required when performing a L2 or L3 Assessment. Penetration testing done at these levels
requires this level of access, which we call "hybrid reviews" or "hybrid penetration tests".  

For example,  
NIST 800-63 considers usernames and Knowledge Based Authentication (KBA) as public information, SMS and
email notifications as "restricted" authenticator types , and passwords as pre-breached. This reality renders
knowledge based authenticators, SMS and email recovery, password history, complexity, and rotation controls
useless. These controls always have been less than helpful, often forcing users to come up with weak
passwords every few months, but with the release of over 5 billion username and password breaches, it's time
to move on.  

Previously, based on ISO 27002 requirements, the ASVS has required blocking multiple simultaneous
sessions. Blocking simultaneous sessions is no longer appropriate, not only as modern users have many
devices or the app is an API without a browser session, but in most of these implementations, the last
authenticator wins, which is often the attacker. This section provides leading guidance on deterring, delaying
and detecting session management attacks using code.  


Note: Using parameterized queries or escaping SQL is not always sufficient; table and column names, ORDER
BY and so on, cannot be escaped. The inclusion of escaped user-supplied data in these fields results in failed
queries or SQL injection.  

Note: The SVG format explicitly allows ECMA script in almost all contexts, so it may not be possible to block all
SVG XSS vectors completely. If SVG upload is required, we strongly recommend either serving these uploaded
files as text/plain or using a separate user supplied content domain to prevent successful XSS from taking over
the application.  

The primary objective of error handling and logging is to provide useful information for the user,
administrators, and incident response teams. The objective is not to create massive amounts of logs, but high
quality logs, with more signal than discarded noise.  

The purpose of error handling is to allow the application to provide security relevant events for monitoring,
triage and escalation. The purpose is not to create logs. When logging security related events, ensure that
there is a purpose to the log, and that it can be distinguished by SIEM or analysis software.  



Create teams and their targets (aka. a project for a team to secure, or a project for a person to own).  
It all depends on the system types:- all - Level 1- applications containing sensitive data, which requires protection - Level 2- most critical applications - Level 3 -- performing high value transactions, containing sensitive medical data, or any application that requires the highest level of trustLET'S START FROM Level1
Automated tools and online scans are unable to complete more than half of the ASVS without human
assistance. If comprehensive test automation for each build is required, then ...  

One of the best ways to use the Application Security Verification Standard is to use it as a blueprint to create a
Secure Coding Checklist specific to your application, platform or organization.  
We should decide: application, platform or organizationAnd be specific.  

Secure Coding Checklist to {specific application, platform or organization} by {who is taking the ownership}  

Level 1 is the bare minimum that all applications should strive for. It is also useful as a first step in a multi-
phase effort or when applications do not store or handle sensitive data and therefore do not need the more
rigorous controls of Level 2 or 3.  

We consider Level 1 the minimum required for all applications.  

The identifiers may change between versions of the standard therefore it is preferable that other documents,
reports, or tools use the format: v<version>-<chapter>.<section>.<requirement>, where: 'version' is the ASVS
version tag. For example: v4.0.2-1.11.3. This could be summarized as v<version>-<requirement_identifier>.
Note: The v preceding the version portion is to be lower case.  

ASVS requirement lists are made available in CSV, JSON, and other formats which may be useful for reference
or programmatic use.  

It may be that the section is not applicable (N/A). E.g. stateless applications may not have session management which would be accepted as ".complied"  
It is not sufficient to simply run a tool and report on the failures; this does not (at all) provide
sufficient evidence that all issues at a certifying level have been tested and tested thoroughly. In case of
dispute, there should be sufficient assurance evidence to demonstrate each and every verified requirement
has indeed been tested.  

Certifying organizations are free to choose the appropriate testing method(s), but should indicate them in a
report.  

ASVS can also be used to define characteristics of secure software.  

Application security professionals must keep up with agile techniques, which means adopting developer tools, learning to code,
and working with developers rather than criticizing the project months after everyone else has moved on.  

The primary objective of error handling and logging is to provide useful information for the user,
administrators, and incident response teams. The objective is not to create massive amounts of logs, but high
quality logs, with more signal than discarded noise.  

The purpose of error handling is to allow the application to provide security relevant events for monitoring,
triage and escalation. The purpose is not to create logs. When logging security related events, ensure that
there is a purpose to the log, and that it can be distinguished by SIEM or analysis software.
Finding malicious code is proof of the negative, which is impossible to completely validate. Best efforts should
be undertaken to ensure that the code has no inherent malicious code or unwanted functionality.
Lead developers should regularly review code check-ins, particularly those that might access time, I/O, or
network functions.  
We recommend the use of threat modeling during design
sprints, for example using the OWASP Cornucopia or similar tools.  
Note: At Level 1, 14.2.1 compliance relates to observations or detections of client-side and other libraries and
components, rather than the more accurate build-time static code analysis or dependency analysis. These
more accurate techniques could be discoverable by interview as required.  
