
# Creating an AI adoption strategy for an enterprise
Artificial intelligence has already proven itself quite impactful in the way organizations operate today. Unlike prior technological advances, its **easy adoption**, **short time- to- value realization** and **versatility of application** are paving the way for citizen developers to create useful applications themselves. This empowers the business users who now automate workflows, easily add functionality atop their favorite applications, get targeted queries answered across multiple datasets almost instantaneously and on their own without the need for a traditional IT function. On one hand, this brings in flexibility and speed to the activities inside an organization, but on the other hand, it raises the risk of unmanaged data leaks and excessive expenses incurred because of unfettered usage.

The focus therefore shifts towards "managing" this innovation and productivity boom so that an organization can encourage greater adoption of AI while being confident about preventing any potential misuse. The rest of the article here summarizes the considerations that must be applied when creating an AI adoption strategy while anticipating and overcoming the unexpected gotchas in a large enterprise. 

##### Table of Contents  
- [The most common AI uses](#the-most-common-ai-uses)
- [The conflicting reality](#the-conflicting-reality)
- [The main stakeholders](#the-main-stakeholders)
- [The basic principles](#the-basic-principles)
    - [The core components](#the-core-components)
- [A proposal](#a-proposal)

## The most common AI uses
Artificial intelligence is advancing at an ever- accelerating pace and break- through innovations in their capability are almost a staple of everyday news headlines. However if we consider the most rudimentary uses for AI, only a few distinct categories emerge. Note that real- world AI applications may often fall into more than one category mentioned here. 

| Category | Author | Purpose | Example | Included in the AI adoption strategy |
| -- | -- | -- | -- | -- |
| **Vibe- coded app** | Citizen developer | Business users often require their everyday work applications to behave in a more intuitive way and favor greater automation for the labor-intensive part of such interactions. They build apps often with bespoke user interfaces that favor productivity. AI is used to create the app but AI is not used inside the app.  | The procurement manager wishes to auto-approve a large inflow of low- value purchase orders to specific pre-approved vendors, thus saving a considerable amount of time. | ✅ |
| **Generative AI** | Citizen developer | Users want to bring generative AI capabilities to their daily work by getting them triggered autonomously within the applications that they normally use or by an AI agent that makes helpful suggestions. | The warehouse receiving clerk receives daily emails from vendors informing the company of the schedule and size of the shipments they are making in the coming weeks. The clert plans the warehouse space and workers in advance based on this information. She creates an agent that reads the inbox and makes a daily summary against each purchase order being received that is used to post advanced shipment notices to the ERP. | ✅ |
| **Chatbot** | Citizen developer | Users raise questions in natural language to gain insights into data that would otherwise be hard to analyze, possibly because the data is spread in disconnected data sets. Chatbots may be created unique to a functional domain or even a sub-team inside it, based on the data they need access to. | An order desk employee needs to answer a call from a customer regarding the progress of a customer order that can be gleaned from a CRM system in which the order is booked, an ERP system which tracks the execution of manufactured units and a transportation management system to track shipping status. She has access to these systems to the extent needed to track progress of orders. | ✅ |
| **Pre- built** | Vendor | Applications being used by business users already have standard AI functionality embedded inside. These are typically outside the ambit of a company's AI adoption strategy because the interaction with the LLMs happens natively inside the application and often cannot be intercepted. Vendors usually provide an assurance of data privacy as part of their customer service agreement. | A recently procured product life cycle management system contains functionality to identify closely resembling products based on standard attributes like bill of materials, variants like colors & shapes, technical specifications etc. The feature is used to remove duplicates and keep the product catalog lean. The admin needs to simply flip a switch to enable the functionality before use. | ❌ |
| **Custom data model** | Data analysts | Applications built to use AI in a non-natural language based context, usually by creating models from scratch based on customized and private data sets to yield predictions or forecasts. As this is often done by data analysts in the IT function who are expected to be fluent with AI, safeguards are assumed to have been placed already. | A company needs to set its yearly sales targets for the coming period. It analyzes its annual sales data for its flagship products, according to a particular machine learning algorithm, that looks at narrow behavioral traits of its niche customer base. | ❌ |


## The conflicting reality
As may be seen from the use cases above, deriving the true value from AI requires it to first assimilate facts from a wide range of data sources as well as sufficiently large samples of data in those sources, eventually yielding results that are holistic in nature. But if an organization has not yet created an AI adoption strategy, it is likely that they are yet to strike the right balance between conflicting forces that push them to either adopt AI or exercise caution against it. 

``` mermaid
kanban
    Pros[<h3>Factors favoring AI adoption</h3>]
        [<span style="font-size:xx-large">👑</span><p>Leadership push</p>]
        [<span style="font-size:xx-large">🧑‍💻</span><p>Enthusiastic citizen developers</p>]
    Cons[<h3>Factors warranting caution</h3>]
        [<span style="font-size:xx-large">🗗</span><p>Heterogenous application landscape</p>]
        [<span style="font-size:xx-large">⁉️</span><p>Unprepared for governance</p>]
```

* **Leadership push**. The senior management are coerced by their shareholders to demonstrate "competitiveness" or adopt a more "tech- embracing attitude" with respect to their peers. 
* **Enthusiastic citizen developers**. Frontline workers in the business have had a positive experience with AI and are raring to create or use even more tools to enhance their productivity. 
* **Heterogenous application landscape**. There may be too many, and often duplicate, discrete systems that information lives in. Also, not all of them may be in the same state of readiness to safely extract data from.
* **Unprepared for governance**. The IT function has reservations against unbridled use of tokens or leakage of sensitive company data (often intellectual property) to external models or even to unauthorized internal employees. Without sufficient guardrails, they may resist AI exposure.

## The main stakeholders

The following table lays out the primary participants in the AI adoption strategy. While most of the stakeholders may be familiar, the AI- Center of Excellence (AI-CoE) team may be a new construct and needs to be formed in a matrixed way comprising of representatives from multiple functions.

<table cellspacing="0" cellpadding="0">
  <tr>
    <td><pre lang="mermaid"><code>flowchart
    CitizenDev(["Citizen developer"])
    class CitizenDev User_CTZ
    CTZDesc@{ shape: "text", label: "The frontline worker who uses AI and creates applications for an individual or a team use to increase productivity." }
    subgraph CTZExpectation["What the stakeholder expects"]
        CTZExpectation_@{ shape: "rect", label: "Clear directions to follow so that the app thus created is safe, performs optimally and helps to boost productivity." }
    end;
    subgraph CTZResponsibility["What is expected of the stakeholder"]
        CTZResponsibility_@{ shape: "rect", label: "Creates applications based on best practices outlined by the AI-CoE while taking appropriate approvals whenever required." }
    end;

    CitizenDev & CTZDesc ~~~ CTZExpectation & CTZResponsibility

    classDef User_CTZ stroke:LightBlue, fill:LightBlue, font-family:Arial, color:Black, font-weight:Bold
    </code></pre></td>
    <td><pre lang="mermaid"><code>flowchart
    BizUser([Business user])
    class BizUser User_BIZ
    BIZDesc@{ shape: "text", label: "The business user who is going to use the app created by the citizen developer. This individual is different than the citizen developer for apps created for a group of people." }
    subgraph BIZExpectation["What the stakeholder expects"]
        BIZExpectation_@{ shape: "rect", label: "The app is easy to use and works well. In case of obvious inaccuracies in the AI- created suggestions, it is possible to provide (hopefully in-app) feedback the citizen developer for improving it." }
    end;
    subgraph BIZResponsibility["What is expected of the stakeholder"]
        BIZResponsibility_@{ shape: "rect", label: "AI suggestions to change any line of business app data are always vetted by this person, who remains accountable for converting the suggestion into actions or data updates." }
    end;

    BizUser & BIZDesc ~~~ BIZExpectation & BIZResponsibility

    classDef User_BIZ stroke:Pink, fill:Pink, font-family:Arial, color:Black, font-weight:Bold
    </code></pre></td>
  </tr>
  <tr>
    <td><pre lang="mermaid"><code>flowchart
    DATAUser([Data steward])
    class DATAUser User_DATA
    DATADesc@{ shape: "text", label: "The data analysts for the data sources spread across line of business apps. They could be either from business or from IT functions." }
    subgraph DATAExpectation["What the stakeholder expects"]
        DATAExpectation_@{ shape: "rect", label: "Data classifications are adhered to when interacting with AI systems. Sensitive data never get leaked outside." }
    end;
    subgraph DATAResponsibility["What is expected of the stakeholder"]
        DATAResponsibility_@{ shape: "rect", label: "Understands the underlying data and provides input for classifying it into the right categories." }
    end;
    
    DATAUser & DATADesc ~~~ DATAExpectation & DATAResponsibility

    classDef User_DATA stroke:Orange, fill:Orange, font-family:Arial, color:Black, font-weight:Bold
    </code></pre></td>
    <td><pre lang="mermaid"><code>flowchart
    DADMUser([Data administrator])
    class DADMUser User_DADM
    DADMDesc@{ shape: "text", label: "The data administrator controls the data that is directly queried / exposed for consumption by an AI application." }
    subgraph DADMExpectation["What the stakeholder expects"]
        DADMExpectation_@{ shape: "rect", label: "Following the best practices sufficiently safeguards the data from misuse by the AI app." }
    end;
    subgraph DADMResponsibility["What is expected of the stakeholder"]
        DADMResponsibility_@{ shape: "rect", label: "Data is classified correctly and data access governance for individuals or service accounts follow the usual governance." }
    end;

    DADMUser & DADMDesc ~~~ DADMExpectation & DADMResponsibility

    classDef User_DADM stroke:Blue, fill:Blue, color: White, font-family:Arial, font-weight:Bold
    </code></pre></td>
  </tr>
  <tr>
    <td><pre lang="mermaid"><code>flowchart
    COEUser([AI-CoE])
    class COEUser User_COE
    COEDesc@{ shape: "text", label: "The team that is responsible to craft and maintain the company's AI Adoption strategy. This team is made of representatives from IT, Legal, Business, Cybersecurity, Risk & Compliance etc." }
    subgraph COEExpectation["What the stakeholder the expects"]
        COEExpectation_@{ shape: "rect", label: "The senior leadership supports the adoption of the governance approach proposed by the AI-CoE." }
    end;
    subgraph COEResponsibility["What is expected of stakeholder"]
        COEResponsibility_@{ shape: "rect", label: "Formulate org- wide policies and build safeguards to use AI in a safe and efficient manner." }
    end;

    COEUser & COEDesc ~~~ COEExpectation & COEResponsibility

    classDef User_COE stroke:Black, fill:Black, color: White, font-family:Arial, font-weight:Bold
    </code></pre></td>
    <td><pre lang="mermaid"><code>flowchart
    LoBADMUser([LoB administrator])
    class LoBADMUser User_LoBADM
    LoBADMDesc@{ shape: "text", label: "The administrator (typically, in the IT function) of the business apps used directly by business users to track activities inside the company." }
    subgraph LoBADMExpectation["What the stakeholder expects"]
        LoBADMExpectation_@{ shape: "rect", label: "User-level access controls configured in the app are respected even when the data leaves the system." }
    end;
    subgraph LoBADMResponsibility["What is expected of the stakeholder"]
        LoBADMResponsibility_@{ shape: "rect", label: "Provide inputs for which data can be accessed by which user / role." }
    end;

    LoBADMUser & LoBADMDesc ~~~ LoBADMExpectation & LoBADMResponsibility

    classDef User_LoBADM stroke:Magenta, fill:Magenta, color: White, font-family:Arial, font-weight:Bold
    </code></pre></td>
  </tr>
</table>

## The basic principles
* data governance
* token usage
* check deck
* feedback loop ensuring continuous value delivery, at least initially
* auditability and accountability
* AI is a new beast- even the leaders appear unsure- so, no assumptions!


### The core components


## A proposal

### Interactions between the components

### The full picture

``` mermaid
 graph LR;
 A[Wiki supports Mermaid] --> B[Visit <a href="https://mermaidjs.github.io">https://mermaidjs.github.io</a> for Mermaid syntax];
```

## Raw
Inputs to AI architecture

EU AI Act

Token usage includes AI tool credits like Copilot credits (check SKU first)


Internal LLM: token conscious, sensitiveity of external LLMs gaining knowledge, not to use overly complicated apps for simple tasks

Token usage should be part of the telemetry just so that the budget controls can be implemented at the line of business level.

Multiplexing requires user license to be granted to the managed app, when updating it. Most vendors are okay to not require licenses if the "right" channels are used to push the data out of the system.

Why create a data gateway?
- The reasoning for data gateway is simplicity of maintainance, access definitions & transformation consolidation. This should not prevent apps from direct access to the individual managed apps, IF that requirement is felt.
- Consolidation of different data sources
- Unified way to give access- One security gate.
- Avoid expensive API throttled direct connections to the managed apps
- Older applications may not have modern safety nets to make point to point solutions
- if multiple systems (of ERP, say) exist, citizen developers tend to make managed app- specific applications.

IT must approve updates to managed applications because
- native validation logic must not be bypassed
- updates might require additional approvals in a matrixed organization

QUESTION
What considerations favor the creation of an Internal on-premises LLM?
How can the low code platform ensure that an app is not created at a too low level on the System of record.
Talk to Vinod about how user access control is enforced.



# Copy from current Wiki

``` mermaid
flowchart
    CitizenDev([Citizen developer])
    class CitizenDev User_CTZ
    BizUser([Business user])
    class BizUser User_BIZ
    CoE([AI-CoE])
    class CoE User_COE

    subgraph Legend[**LEGEND**]
        direction TB
        AiArtifact@{ shape: doc, label: "Public knowledge base artifact" }
        class AiArtifact AiArtifacts
        AiApp@{ shape: doc, label: "AI app type. See <a href="https://teams.microsoft.com/l/message/19:eGry29yW3XgeT0FZGbV5-dCd26T4fjsacj0XkXT2Z001@thread.tacv2/1788161732377?tenantId=5a783410-682d-4564-b908-bb78d5afb2fe&groupId=5b49319a-5046-4872-8dd8-39756ba5253a&parentMessageId=1788161732377&teamName=FLS%20AI%20Strategy&channelName=Strategy%20formulation&createdTime=1788161732377">Categories</a>" }
        class AiApp AiApps
        Team(["User / team"])
        Database@{ shape: cyl, label: "Data participating directly in the AI architecture" }
        class Database Database
        subgraph Component[ ]
            Comp@{ shape: "text", label: "Component or subcomponent" }
        end;
    end;
    style Legend stroke:Black, stroke-width: 5px, fill:None, color:blue, font-family:Fantasy, Trebuchet MS

    subgraph CompanyData[Organization data]
        subgraph GoldenSystemOfRecord[Data gateway on Golden system of record e.g. Snowflake]
            DataStewards(["Data steward"])
            class DataStewards User_DATA
            DataAdmin([Data admin])
            class DataAdmin User_DADM

            DataClassifications@{ shape: cyl, label: "Data classifications" }
            class DataClassifications Database
            SnowflakeAccessControl@{ shape: cyl, label: "Access control" }
            class SnowflakeAccessControl Database

            DataCatalog@{ shape: doc, label: "Catalog of data exposed" }
            class DataCatalog AiArtifacts

            DataLlmSuite@{ shape: doc, label: "Built-in generative AI suite<br/> (see <a href="https://www.snowflake.com/en/product/features/cortex/">Snowflake Cortex AI</a>)" }
            class DataLlmSuite AiArtifacts

            DataAdmin -- configures --> DataClassifications
            DataAdmin -- configures --> SnowflakeAccessControl 
            DataStewards -. provides inputs .-> DataClassifications
        end
        style GoldenSystemOfRecord color:blue, font-family:Fantasy, Trebuchet MS
        subgraph Organized[Managed applications]
            ERPs@{ shape: h-cyl, label: "ERPs- <br/>e.g. D365 F & O, Oracle, Epicor" }
            CRM@{ shape: h-cyl, label: "CRMs- <br/>e.g. D365 CE" }
            PLM@{ shape: h-cyl, label: "PLM- <br/>e.g. Enovia" }
            HR@{ shape: h-cyl, label: "HR- <br/>e.g. Workday" }
            Procurement@{ shape: h-cyl, label: "Procurement- <br/>e.g. Coupa" }
            SupportSystem@{ shape: h-cyl, label: "Business Support- <br/>e.g. ServiceNow" }
            Pricing@{ shape: h-cyl, label: "Pricing- <br/>e.g. PSP, SPC etc" }
            LoBADMUser([LoB administrator])
            class LoBADMUser User_LoBADM
            BizAppsAccessControl@{ shape: cyl, label: "Access control" }
            class BizAppsAccessControl Database

            ERPs & CRM & PLM & HR & Procurement & SupportSystem & Pricing ~~~ LoBADMUser & BizAppsAccessControl

            LoBADMUser -- configures --> BizAppsAccessControl
        end
        style Organized color:blue, font-family:Fantasy, Trebuchet MS
        subgraph Unstructured[Unstructured]
            Sharepoint@{ shape: h-cyl, label: "Specific sharepoint locations" }
            SharedMailbox@{ shape: h-cyl, label: "Shared mailboxes" }
            FileShares@{ shape: h-cyl, label: "File shares (FTP etc.)" }
        end
        style Unstructured color:blue, font-family:Fantasy, Trebuchet M
        subgraph UnmanagedData[Unmanaged data]
            PrivateEmail@{ shape: h-cyl, label: "Private emails" }
            Extract@{ shape: h-cyl, label: "Data extracts from managed systems" }
        end
        style UnmanagedData color:blue, font-family:Fantasy, Trebuchet MS

        Organized -. periodically sync .-> GoldenSystemOfRecord
        Unstructured -. export files on creation/ update .-> GoldenSystemOfRecord
    end
    style CompanyData stroke:None, fill:#f7e0c6, color:blue, font-family:Fantasy, Trebuchet MS

    subgraph AIProject[AI Project hub]
        subgraph Apps[AI apps]
            VibeCodedApp@{ shape: doc, label: "**Vibe-coded application**<ul><li>AI - Assisted Build (category 1)</li></ul>" }
            class VibeCodedApp AiApps
            LLMProj@{ shape: doc, label: "**Projects requiring use of generative AI**<ul><li>AI - Integrated Application (category 2)</li><li>AI Agent / Automation</code> (category 3)</li></ul>" }
            class LLMProj AiApps
            Chatbot@{ shape: doc, label: "**Make data human - queryable**<ul><li>Direct AI Tool Usage (category 4)</li></ul>" }
            class Chatbot AiApps
        end;
        AppCatalog@{ shape: doc, label: "Catalog of projects, illustrations of best practice applications" }
        class AppCatalog AiArtifacts
        AppMetrics@{ shape: doc, label: "Dashboard of usage of apps and user confidence in it, based on evals being logged." }
        class AppMetrics AiArtifacts
        MustUpdateManagedApp@{ shape: diamond, label: "?" }
        UpdateApprovedByUser@{ shape: diamond, label: "?" }
        SourceControl@{ shape: cyl, label: "Source control for apps" }
        class SourceControl Database

        VibeCodedApp & LLMProj -- must update managed App? --> MustUpdateManagedApp -- Business user has approved changes to be made? (Human- in- the- loop) --> UpdateApprovedByUser
        Apps -- saves to --> SourceControl
    end;
    style AIProject stroke:None, fill:#ebfcfc, color:blue, font-family:Fantasy, Trebuchet MS

    subgraph AIGateway[AI gateway]
        TokenGovernance@{ shape: cyl, label: "Token / AI credits governance" }
        class TokenGovernance Database
        RedactPolicies@{ shape: cyl, label: "Data redaction or omission policies" }
        class RedactPolicies Database
        ApprovalsForExternalLlms@{ shape: cyl, label: "Approvals for external LLM calls per app" }
        class ApprovalsForExternalLlms Database
        TokenUseApproved@{ shape: diamond, label: "?" }
        ExternalLLMApproved@{ shape: diamond, label: "?" }
        CallLogAsEvals@{ shape: cyl, label: "Call logs with details: <ol><li>request</li><li>response</li><li>token cost</li><li>User acceptance of AI suggestion</li></ol>" }
        class CallLogAsEvals Database
        subgraph MakeCall[Query LLM]
             RedactData[Redact/ omit sensitive data]
             class RedactData Action
             PlaceCall[Place call]
             GathersUserFeedback[Gathers user feedback, <ul><li>by detecting extent to which user adopts suggestion,</li><li>or, by explicitly asking user in the app.</li></ul>]
             class GathersUserFeedback Action
             RedactData --> PlaceCall --> GathersUserFeedback
             class PlaceCall Action
        end
        style MakeCall color:blue, font-family:Fantasy, Trebuchet MS
        BestPractices@{ shape: doc, label: "Best practices for AI projects, architecture, etc." }
        class BestPractices AiArtifacts

        RedactData -. references .-> RedactPolicies
        GathersUserFeedback -- saves eval --> CallLogAsEvals
    end
    style AIGateway stroke:None, fill:#f8ebfa, color:blue, font-family:Fantasy, Trebuchet MS

    subgraph Models["AI Models"]
        ExternalModel@{ shape: braces, label: "External LLMs<br/>Claude, Copilot, ChatGPT etc."}
        InternalModel@{ shape: doc, label: "Internal LLM" }  
        class InternalModel AiArtifacts
    end
    style Models stroke:None, fill:#c7fcd6, color:blue, font-family:Fantasy, Trebuchet MS

    Legend ~~~ CompanyData 
    BizUser ~~~ CitizenDev

    CitizenDev -. references .-> BestPractices & DataCatalog
    CitizenDev -- references & enriches --> AppCatalog 
    CitizenDev -- collects metrics and continually improves solution --> AppMetrics

    ExternalLLMNeeded@{ shape: diamond, label: "?" }
    CitizenDev -- if app makes direct calls to external LLM during runtime, approval is needed. Provide the (sensitive) data points to be sent as inputs to the LLM and the justification thereof. --> ExternalLLMNeeded
    ExternalLLMNeeded <-. interacts .-> CoE
    ExternalLLMNeeded -- Approved. Creates application --> AIProject

    GoldenSystemOfRecord -- securely provides data based on the app user's credential --> AIProject
    DataStewards <-. interfaces .-> BizAppAdmin
    DataClassifications -- dictates --> RedactPolicies
    BizAppsAccessControl -- dictates --> SnowflakeAccessControl
    UnmanagedData -- **RISKY! NOT IT SUPPORTED.** --> LLMProj
    Snowflake -- maintains --> DataCatalog
    DataLlmSuite <-. interacts, for sensitive data .-> InternalModel

    UpdateApprovedByUser -- yes. Perform update using app user's credentials to support auditability. This part of the app may require review by IT. --> Organized
    UpdateApprovedByUser -. app takes user approval and logs it internally .-> BizUser
    AppCatalog -. references .-> BestPractices
    Chatbot -- queries --> DataLlmSuite

    BizUser -- calls or uses application --> AIProject 
    LLMProj -- **RISKY! NOT IT SUPPORTED.** --> ExternalModel
    GoldenSystemOfRecord -. incremental updates to keep internal LLM in sync .-> InternalModel
    LLMProj -- Yes. External LLM needed? --> ExternalLLMApproved -. references .-> ApprovalsForExternalLlms
    ExternalLLMApproved -- Yes. Token use within limits? --> TokenUseApproved -. references .-> TokenGovernance 
    ExternalLLMApproved -- No --> MakeCall
    TokenUseApproved -- Yes --> MakeCall
    AppMetrics -. pulls data from .-> CallLogAsEvals

    PlaceCall <-. interacts .-> Models
    BizUser -. gives feedback for the AI suggestion .-> GathersUserFeedback

    CoE -- configures --> TokenGovernance
    CoE -- configures --> ApprovalsForExternalLlms
    CoE -- maintains --> InternalModel
    CoE -- maintains and enriches --> BestPractices
    CoE -- routinely check for low user satisfaction and continually improves --> CallLogAsEvals
    CoE -- maintains --> AppMetrics 


    classDef User_CTZ stroke:LightBlue, fill:LightBlue, font-family:Arial, color:Black
    classDef User_BIZ stroke:Pink, fill:Pink, font-family:Arial, color:Black
    classDef User_DATA stroke:Orange, fill:Orange, font-family:Arial, color:Black
    classDef User_COE stroke:Black, fill:Black, color: White, font-family:Arial
    classDef User_DADM stroke:Blue, fill:Blue, color: White, font-family:Arial
    classDef User_LoBADMUser stroke:Magenta, fill:Magenta, color: White, font-family:Arial
    classDef AiArtifacts stroke: Black, fill: Red, color: White, font-family: Arial, font-weight: bold, text-align:justify, text-justify:inter-word
    classDef AiApps stroke: Blue, fill: Blue, color: White, font-family: Arial, font-weight: bold, text-align:justify, text-justify:inter-word
    classDef Action stroke:None, fill: #f6f0f7, color:blue, font-family:Tahoma, text-align:justify, text-justify:inter-word
    classDef SG stroke:None, fill:#ffffe6, color:blue, font-family:Fantasy, Trebuchet MS
    classDef Database stroke: Brown, stroke-width: 3px, text-align:justify, text-justify:inter-word
```



