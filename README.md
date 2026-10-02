# Community Lost & Found Matching Network – SE Lab
 
**SRN:** PES1UG24CS305
 
## Overview
 
This repository holds my Software Engineering lab work for the Community Lost & Found Matching Network. The system helps people reunite with lost items. It extracts visual and text tags from item photos and descriptions, matches lost and found items by tags and location, and asks security questions so that only the real owner can claim an item.
 
## Actors
 
- Finder / Owner
- Community Admin
---
 
## Lab 1: Requirements Engineering & UML Use-Case Modelling
 
Files are in the root of the repository.
 
- **Requirements_Table_PES1UG24CS305.pdf** – 5 functional and 2 non-functional requirements, each with an ID, type, description, priority, acceptance criteria and rationale.
- **Use-Case_Diagram_PES1UG24CS305.pdf** – UML use-case diagram showing the actors and main use cases, including `<<include>>` and `<<extend>>` relationships.
- **Use-Case Flow_PES1UG24CS305.pdf** – one-page flow for a core use case, with preconditions, postconditions, the main success scenario and one alternate flow.
---
 
## Lab 3: Component Modelling & Architectural Pattern Selection
 
Files are in the `Lab3/` folder.
 
- **Lab3_Component_Diagram_PES1UG24CS305.png** – UML component diagram of the system.
- **Lab3_Justification_PES1UG24CS305.pdf** – one-page justification for the chosen architecture.
- **Lab3_Component_Diagram_PES1UG24CS305_v2.drawio** – editable source file for the diagram.
### Architecture chosen: Microservices
 
I compared Layered, Client-Server and Microservices, and chose Microservices. Tag extraction from photos is much heavier than the rest of the system, so it needs to scale on its own. Keeping the services separate also means one failing service doesn't bring the whole system down.
 
### Components
 
| Component | What it does |
|---|---|
| Client App (Web / Mobile UI) | Lets users report items, upload photos and answer verification questions |
| Item Management Service | Handles lost/found reports and coordinates the other services |
| Tag Extraction Service | Pulls visual and text tags from photos and descriptions |
| Geo-Matching Service | Matches lost and found items by tags and location |
| Ownership Verification Service | Stores security questions and checks a claimant's answers |
| Item Database | Stores items, tags, locations and user data |
 
### Interfaces
 
| Interface | Provided by | Required by | Type |
|---|---|---|---|
| IItemReport | Item Management Service | Client App | REST API (HTTPS) |
| IVerification | Ownership Verification Service | Client App | REST API (HTTPS) |
| ITagExtraction | Tag Extraction Service | Item Management Service | REST API / async queue |
| IMatchQuery | Geo-Matching Service | Item Management Service | REST API |
| IItemData | Item Database | Item Management Service | SQL queries |
| ILocationQuery | Item Database | Geo-Matching Service | Geo-spatial DB queries |
 
---
 
## Tools Used
 
- draw.io (diagrams.net) for UML diagrams
- Microsoft Word for written documents
 
