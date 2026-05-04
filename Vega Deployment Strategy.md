Vega Deployment Strategy

1) EXECUTIVE SUMMARY

The original Vega deployment strategy was to allow customers to use two non-tech resources to perform physical installation of the Vega lanes and Eero network, then a remote Amazon resource would perform virtual configuration, and launch would be completed by the customer executing a shopping trip to validate overall functionality. Unfortunately, the initial deployment strategy is unadvisable considering design churn and lack of testing performed. It is expected that continuing on this path would have eroded customer trust and perceived quality of the Vega solution.

We seek leadership approval for two initiatives:

1. Resource allocation to scope and develop the self-guided customer deployment tool (BRD forthcoming in Q4 2025).
2. Implementation of Third Party Tech Deployment (3PTD, also referred to as Yellow Badge) resources to manage store launches and teardowns, while developing a self-guided workflow tool for future customer ownership. This phased approach ensures deployment quality while building operational insights needed for successful customer-led installations.


We are seeking alignment due to time sensitivity; deferment of a decision will extend the time we incur 3PTD resource cost and delay customer-owned launches. Additional document will focus on how we plan to enable self-guided customer deployment by TK date, our current working backwards date is to pilot in Q2 2026 and GA in Q3 2026.

A potential high level roadmap is as follows:

Milestone	Description	Date
Vega Launch Pilots	Amazon Dev team on-site and owner of overall store launches. 3PTD owns installation and bring-up.	Q3 2025
3PTD Vega Launches	SCOT TDPM team owns overall launch ownership.
3PTD on-site with escalations to dev teams	Q4 2025
Self-Guided BRD Finalized	Requirements, scope, and resourcing needs are finalized.
Implementation begins.	Q4 2025
Self-Guided Lab Take-Away	Validate the self-guided customer workflow in a lab with 'non-tech' Amazon Blue Badge employees	Q2 2026
Self-Guided Customer Pilot	Customer is selected for self-guided launch pilot
Amazon Dev teams on-site for immediate escalation	Q2 2026
Self-Guided Customer as Plan of Record (POR)	Self-guided installation is standard offering to customers.
Amazon-owned (via 3PTD) store launch offering available to customer with additional fee	Q3 2026

2) Short Term: 3PTD Launches

Vega will leverage existing Just Walk Out (JWO) third-party tech deployment (3PTD) resources currently distributed across North America and United Kingdom. The Vendor Management team has already established robust processes for acquiring and allocating resources which can be directly applied to Vega store deployments. Preferential 3PTD resources will cost approximately $1500 per day which equates to $1500 for a store with up to two lanes and $3000 for a store with up to four lanes. If on-site work requires after hours, weekend work, or travel then the estimated price will increase (see: Appendix B: 3PTD Quotes for reference).

3PTD resources are guided through store launch process by using workflows created by Tech Deployment Project Managers (TDPMs) in the Tech Knowledge Scrolls (TKS) tooling. TKS uses its integration with Claire service to determine the number of intended lanes along with other inputs provided by TDPM during the creation process to generate a workflow specific to that store. The assigned 3PTD resources can then ‘clock-in’ to TKS where they execute all tasks, including physical installation, automated virtual bring-up, on-site validation, and store handover. See Appendix C: TKS Workflow Creation for an example of the Vega workflow creation tool within TKS.

Following existing process, Implementation Managers (IMs) own coordination via the SCOT intake process for when resources and materials are needed on-site to meet customer launch timeline. When 3PTD encounter a technical error they will escalate by cutting a ticket that will initially be directed to embedded until appropriate training material are provided to BLAST or remote TDE engineers who will then be the first point of contact. When 3PTD encounter a non-technical error (material arrival, site access, etc) they will escalate by cutting a ticket that is directed to the TDPM.

The TKS platform's integrated metrics and ticketing system will provide valuable insights into deployment processes. By tracking two primary metrics, the team can systematically improve deployment efficiency: 1) identifying installation and bring-up gaps through escalation rate analysis of sev2 incidents and tickets, and 2) pinpoint opportunities to refine Standard Operating Procedures (SOPs) by recording which steps have the highest variability in completion time and the longest average completion time. These tracking mechanisms will inform strategic decisions about when we can start customer launch pilots.

2.1) Limitations [WIP]

Utilizing 3PTD resources limits our ability to deliver on the original promise that customers will be able to perform ‘tour mode’ (launching a store in one location, then tearing it down, and then launching those same lanes at a different geographical location). Customers that are looking to utilize ‘tour mode’ would require increased touch points from Amazon resources to manage physical effort to relocate the store as well as virtual effort to decommission the existing store and launch the next store. This will have cost implication as each new location will be treated as a complete launch and teardown cycle by 3PTD resources. There is potential for Amazon resources to train a customer with consistent resources performing these tasks but it would need to be on a very limited basis and alignment with BD to only be offered for appropriate customers.

3) Q3 2026: Self-Guided Customer Launches

A self-guided tool will be provided to customers which will enable them to perform a full deployment of a Vega store without direct Amazon interaction. Allowing customers to deploy their own stores would have a total financial impact of greater than $226,000.00 or 1,200hrs of effort across the 150 store launch goal in 2026.

The self-guided tooling will use learnings from the TKS implementation to give customers a workflow that provides the best way to launch a store. TKS is an inappropriate tool for customer usage and new tooling will need to be created to meet customers lack of technical background and experience with Amazon systems. Some changes we will need to incorporate to maintain a high quality launch for non-technical customer persona are: 1) providing high fidelity animated renderings to guide the customer through all installation steps, 2) a ‘scan to attach’ feature where customers are prompted to scan the AssetID of the lane to kickoff all virtual bring-up steps and be obscured behind a progress bar, 3) validations will be manually performed by customers who will be asked to perform a single end-to-end validation event where they will ensure that receipt information is accurate, and 4) built-in escalation mechanism to reach customer service resources.

BRD creation and further deep-dive is necessary to fully understand requirements, design, mechanisms, and appropriate tooling. The following is a non-exhaustive list of high level modifications that will be needed:

* Build and maintain the customer facing tooling to include integration with JWO services and meeting security requirements. There is potential to leverage Guided Workflow Tool (GWT). BRD to follow with scope and dev week estimate.
* Customer on-boarding mechanism (potentially leverage Merchant Portal) to onboard customers and provide access to appropriate stores. There is potential to leverage work being performed by PACT team who are creating an externalized JWO bring-up app for Vision based JWO.
* Mechanism for customer escalations regarding bring-up related issues, including those of the new application. BRD to follow with scope and dev week estimate.
* High-fidelity or ‘CAD-like’ renderings will need to be created to replace existing photos for installation instructions.

3.1) Risks

* Variability - Variety is the bane of standardized process. Amazon Tech Deployment resources are able to adapt to their environment, tools, and devices because they have the training and background to make autonomous decisions. Moving the installation and bring-up steps to the customer means the tooling needs to compensate for the users lack of training. Vega is engaging in frequent design and feature churn to meet customers needs (5G, multiple tagging locations, geographical differences, RF panels, etc) which all need to be incorporated into the tooling. There are many ways we can solve this problem but it’s best to understand that additional customer options drive launch workflow complexity. Decision to proceed with launch is a two-way door where we can always maintain standard JWO launch processes using 3PTD.
* Customer-facing Application - I am unaware of a team within JWO that has a customer facing app on an unmanaged device. Need to ensure we have the right skillset to deliver and then maintain this tool.
* Farm to Table - There is always the chance that some customers don’t want to perform the installation themselves and potentially become a blocker for launch. This is unlikely to dissuade a significant number of opportunities but 3PTD resources could be leveraged, at customer cost, to perform the launch.

Frequently Asked Questions (FAQs)

1) What alternatives were considered?
We evaluated maintaining customer-led physical installations but rejected this approach for three key reasons:

* Design Iteration Management: Current design changes (Vega Gen2.1, networking solutions, crate design, and cabling modifications) create frequent procedure updates that are more efficiently managed by Amazon resources.
* Escalation Complexity: Customer-led installations would require a multi-step escalation path (customer → customer service → development teams), increasing response times, straining development resources.
* Insufficient Testing Data: We lack comprehensive lab testing data for non-technical installations, making it difficult to validate this approach's viability.
* Organizational Changes: Reduction in TDE bandwidth to support remote bring-up.


2) How does this deployment strategy affect Same-Store Mobility Mode (the ability for customer to teardown and bring-up the same store) and Tour Mode (the ability for customer to teardown the store, move to a new location, and bring-up with same hardware)?
Same-Store Mobility is purposefully excluded from the scope of this document due to unique complexities that warrants additional set of requirements that would confuse the deployment strategy. However, it is worth nothing that finalization of a tool for customer-guided launches will have accomplished the bulk of the work necessary to unlock customer-owned redeployments (whether this is seasonal or as part of tour). If we proceed with the creation of this tooling then we should incorporate Mobility and Touring requirements into the BRD to ensure the tooling is built for easy adaptation (mobility ETA: 2026). Note: initial Vega Same-Store Mobility Business Requirements. kickoff is later this week.

3) There are other RFID solutions coming, can they also be included in scope?
Yes*
Design of XCO and other RFID based solutions would appear to be following the same ‘encapsulated’ design as Vega and be prime targets for expanding tooling support. It is expected that services already integrated (potentially fewer?) for the Vega-only scope will be immediately applicable to other solutions. However, the physical installation, workflow steps, and validations will be different and require additional effort. We will need to keep open communication between teams to ensure that future solutions are built to incorporate this tooling.

4) Are we going to train 3PTD on how to launch a store before deploying?
We are going to utilize 3PTD's already existing training set on how to escalate and use TKS workflows to launch stores. We will not be providing training material specific to Vega so as to simulate the customer experience and identify those gaps. This allows us to escalate within Amazon quickly to meet launch dates for customers prior to enabling to customer-owned launches.

5) What additional features could the app incorporate?
Potential expansion opportunities are many (3PCC integration, self-guided debugging, paradigm shift to managing a fleet of Vega lanes across multiple store locations, etc) but would require dev resource commitment for development and KTLO operations. Initial work will focus on our commitment to a standardized bring-up solution and exclude this scope drift.

6) How will we track this change in deployment strategy?
We will remove the existing KingPin goal:

* KingPin Goal 828142: Gate Pod can be set up and validated by 1 JWO team member or JWO-trained contractor (either onsite or remote), with the assistance of 2 non-technical resources provided by the retailer, within a standard 8-hour work day. Original due date 09/2024.

And create two new ones:

* KingPin Goal TK1: Vega Gen2.X lanes can be installed and validated by two third-party tech deployment (3PTD) resources within a standard 8-hour work day for up to two lanes and in two standard 8-hour work days for up to four lanes. Due date 11/28/2025.
* KingPin Goal TK2: Pilot a Vega Gen2.X lane installation and validation by the customer through a self-guided workflow tool within a standard 8-hours work day. Due date Q2 2026.

Appendix A: High Level Workflow Diagram

Link to Figma Board
High Level workflow diagram showing which partners are involved with the launch and the scope of work that are executed by 3PTD or eventually the customer. 


Appendix B: 3PTD Quotes

Note: This is for standard work hours and additional expenses are expected for late hours or weekend work.
NA-AA-388
NA-AA-330


Appendix C: TKS Workflow Creation

Below is an example of the end-to-end process required for a Tech Deployment Operations Specialist to create a TKS workflow that is used by 3PTD to guide store launch. https://prod.htpost.msto-tech-integration.amazon.dev/VegaWorkflowCreator



Appendix D: Additional resources

Design Review: Vega Gen2 Bring-Up and Break-Fix
TKS Workflow Creation for Vega
