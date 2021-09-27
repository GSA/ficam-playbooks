---

layout: page
navtitle: Digital Identity Risk Assessment
title: DIRA Agency Plays
collection: playbooks
permalink: DIRA/plays/
sticky_sidenav: true
sidenav: DIRA

subnav:
  - text: Play 1
    href: #play-1
  - text: Play 2
    href: #play-2
  - text: Play 3
    href: #play-3
  - text: Play 4
    href: #play-4
  - text: Play 5
    href: #play-5
  - text: Play 6
    href: #play-6

---

This section introduces six plays for your agency to create efficient and consistent processes for a DIRA. 

## Play 1: Streamline Risk Management and Assessment Processes

The Risk Management Framework (RMF) forms the basis of your agency application Assessment and Authorization (A&A) lifecycle. A DIRA process integrates into the routine phases of the RMF to streamline processes and enables efficient reuse of application and agency resources. Figure 9 shows an alignment of this playbook’s example DIRA process steps with the RMF. 

[![Figure 9 is a graphic representation of the DIRA process aligned with the NIST Risk Management Framework Phase. There are three concentric circles. Continuous monitoring on the outermost circle with continuous arrows representing a continuous process. The two inner circles represent the NIST RMF process aligned with DIRA. DIRA Step 1 Identify Users, Transactions, and Roles aligns with RMF Phase Categorize System. DIRA Step 2 Identify Risks and Assurance Levels aligns with RMF Phase Selecting Controls. DIRA Step 3 Determine steps to Meet Assurance Levels aligns with RMF Phase Implement Controls. DIRA Step 4 Finalize digital identity assessment statement aligns with RMF Phase Assess Controls. There is no DIRA Step that aligns with RMF Phase Authorize. DIRA Step 5 Reassess aligns with RMF Phase Monitor.](../../assets/dira/process_DIRAFigure9.png)](../../assets/DIRA/process_DIRA Figure9.png){:target="_blank"}{:rel="noopener noreferrer"}

Step 1 of the example DIRA process happens in the Categorize phase. When categorizing a system (refer to Federal Information Processing Standards Publication 199 (FIPS 199):
Standards for Security Categorization of Federal Information and Information Systems, Section 3, Categorization of Information and Information Systems), application owners and security officers identify overall system data types and assign impact levels for each of the confidentiality, integrity, and availability security objectives.  

A Privacy Threshold Analysis (PTA) is typically included in this phase. The identification of the DIRA IALs, AALs, and FALs directly correlates to the collection of PII; who has access to what information; whether information is self-asserted or verified; and the risks of excessive identity proofing. 

{% include alert-info.html heading="Key Point" content="Align Step 1 in a DIRA process with the Categorize System phase of the Risk Management Framework." %}

Meanwhile, Step 4 of the example DIRA process aligns with the Assessment phase. The Digital Identity Acceptance Statement must include the IALs, AALs, and FALs where the application was assessed and the implementations made.  

Figure 10 explains the DIRA process through the Assessment phase.

[![Figure 10 is a graphic representation of the digital identity risk assessment process. Step 1 is Determine User Type. Step 2 is Define Transactions. Step 3 is Determine Impact Level for Transactions. Step 4 is Determine Assurance Levels. Step 5 is Map Transactions to Roles. Step 6 is Implement the Technology. Step 7 is Validate Requirements. Step 8 is Perform Periodic Reassessments.](../../assets/dira/process_DIRAFigure10.png)](../../assets/DIRA/process_DIRA Figure10.png){:target="_blank"}{:rel="noopener noreferrer"}

Figure 11 provides additional detail about the DIRA process.  

[![Figure 11 is an arrow shaped graphic that depicts the six phases of the DIRA process flow. The first phase is Data Collection. The second phase is Analysis. The third phase is Review. The fourth phase is Implementation Determination. The fifth phase is Concurrence. The sixth phase is Ongoing Assessment. There is an arrow head pointing right on the right side of the sixth phase.](../../assets/dira/process_DIRAFigure11.png)](../../assets/DIRA/process_DIRA Figure11.png){:target="_blank"}{:rel="noopener noreferrer"}

## Play 2: Add Context for the Mission

Context is powerful when assessing risks, making agency risk decisions, and engaging across multi-disciplinary agency stakeholders. Standard and general government-wide policies set the foundation for many agency activities but are written for broad mission areas. Translate user types, transactions, DIRA impact levels, and risk statements into words that are applicable and useful to your agency. 

{% include alert-info.html heading="Key Point" content="Tailor context to your mission to support enterprise risk management discussions." %}

Table 4 provides examples of how agencies add agency-specific terms or context for user types, transactions, and impact levels. 

**Table 4: Example Definitions and Agency Context**

| Assessment Input | Generic Definition | Definition with Agency Context |
| ----------- | ------------ | ---------------------------------- |
| User Type | Organizational User | Employee or agency contractor with a federal agency email address (@agency.gov or @agency.mil) | 
| User Type | Non-Organizational User | Fiscal agent, grant beneficiary, veteran, healthcare worker, or public citizen | 
| Transaction | Export | Employee or agency contractors export data for use outside of the application | 
| Impact Level | Serious Injury or Death | Impact depends on whether the application provides access to law enforcement information that identifies a confidential person (i.e., improperly disclosing a confidential person’s identity puts them in physical danger) | 
| Impact Level | Harm to Agency Programs or Public Interests | Impact depends on the application’s function and its importance to agency operations | 

Table 5 provides an example of how two agencies apply context to Transactions and Impact Levels. 

**Table 5: Example Transactions and Impact Levels**

| Impact Category | Scope of Potential Risk | Agency Context: As a result of a wrong user accessing data in an application, … | User Type | Transaction Type | Agency Impact Definition |
| ----------- | ------------ | ---------------- | ----------- | ------------ | ------------------ |
| Personal Safety | Serious injury or death | Physical injury or death could occur | Organizational User | Employee or agency-contractor exports data for use outside of the system | Impact depends on whether the application provides access to law enforcement information that identifies a confidential informant (i.e., improperly disclosing a confidential criminal informant’s identity puts them in physical danger) |
| Harm to Agency Programs or Public Interests | Adverse effect on organizational operations | The agency’s mission essential functions is adversely impacted | Non-Organizational User | Individual retrieves tax information (PII) | Impact depends on the application’s function and its importance  to agency operations |

## Play 3: Use Templates 

It’s a best practice that agencies develop standardized templates to promote consistency in procedures for digital identity risk assessments. Example templates can be as simple as: 
-	Visual informational guides for what a DIRA is,
-	Informational guides on risks, 
-	Simple spreadsheets or digital surveys, and 
-	Digital Identity Acceptance Statements. 

The [Digital Identity Acceptance Statement template](../../docs/dira-dias-template.docx){:target="_blank"} provides an example DIAS for agencies.   

## Play 4: Shortcut Decision Trees

All federal applications that perform digital transactions and require identity proofing or authentication require a Digital Identity Acceptance Statement, regardless of how the system is hosted. However, not all federal applications require the full example DIRA process and efforts.

Table 6 provides an example shortcut guide for determining whether to perform a full DIRA process based on application characteristics. IAL, AAL, and FAL levels in this table are examples. Applications must follow agency policies, which may be more stringent than the examples in this table.

**Table 6: DIRA Shortcut Guide**

| Application Characteristics | DIRA Required? | Minimum NIST SP 800-63 IAL, AAL, FAL Levels |
| ---------------------- | ------------ | ------------------ |
| The application has no external network connectivity, is physically isolated, and is located in a protected space. | No | N/A | 
| The application leverages the agency enterprise single sign on (SSO)/enterprise access manager for authentication of employees and contractors. | Yes | Requires proof of identity (IAL3; satisfied by the full PIV issuance processes, in accordance with government-wide policy and Office of Personnel Management (OPM) credentialing requirements for federal executive branch employees and contractors). Multi-factor authentication to agency application (AAL2) federation between agency applications (FAL2).<br><br> Additionally, requires affiliation as a federal employee or contractor. | 
| Data and other resources available are approved for public release, are intended to be freely shared, and public users aren’t required to create accounts to access this information.<br><br>Examples include:<br> <li> Agency primary websites (i.e., www.gsa.gov),</li><li>Informational websites, and</li><li>Open government APIs.</li> | No | Public users don’t create accounts or login. <br><br>Agency-affiliated privileged users with permissions to edit content still require higher IAL and a minimum AAL2 (two-factor). | 
| Data and other resources are intended for public release. Doesn’t include any controlled unclassified information, but allows public users to create accounts to better support the public user’s experience. | Yes | Doesn’t require proof of a real-life identity (IA 1). Single or multi-factor authentication (AAL1).| 
| Allows public users to input and access their own personally identifiable information (PII) or protected health information (PHI) for informational purposes.  The information isn’t required to be verified. The application doesn’t allow public users to access anyone else’s PII or PHI. | Yes | Doesn’t require proof of a real-life identity (IAL1). Multi-factor authentication (AAL2). | 

## Play 5: Leverage Existing Agency Tools

Leverage existing tools at your agency to automate and create repeatable and consistent DIRA processes. For example, one agency integrated the DIRA process into its Governance Risk and Compliance (GRC) tool. The agency was able to simplify integration with the Risk Management Framework (RMF) lifecycle and support the inclusion of the DIAS with other system artifacts. Agencies that use commercial GRC tools should consider integrating DIRAs into the workflows. 

## Play 6: Less Is More

A common assumption when building or buying applications for missions is that all users need accounts. Take the opportunity during the DIRA process to consider the application processes and functionality needed. Consider the mission, applications needs, and the two example questions below: 
1.	Do all users need accounts?  
2.	How many users are regularly recurring returning users? 

Reconsider the business process carefully and validate the current and future designs using data on the returning users, transaction volumes, and privacy principles. 
-	Design the business process for the user to submit information without requiring an account,
-	Limit the information required to create the account, and
-	Make most of the information requested optional.

{% include alert-info.html heading="Key Point" content="Some public, business, or partner users may only interact with the government process and application once a year or less.<br><br> Revisit your process and application, and allow users to complete the transaction once before opting in to create an account." %}
