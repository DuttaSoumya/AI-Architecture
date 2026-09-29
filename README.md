
# Crafting a governance strategy when democratizing AI adoption in an enterprise
Artificial intelligence has already proven itself quite impactful in the way organizations operate today. Unlike prior technological advances, its **easy adoption**, **short time- to- value realization** and **versatility of application** are paving the way for citizen developers to create useful applications themselves. This empowers the business users who now automate workflows, easily add functionality atop their favorite applications, get targeted queries answered across multiple datasets almost instantaneously and on their own without the need for a traditional IT function. On one hand, this brings in flexibility and speed to the activities inside an organization, but on the other hand, it raises the risk of unmanaged data leaks and excessive expenses incurred because of unfettered usage.

The focus therefore shifts towards "managing" this innovation and productivity boom so that an organization can encourage greater adoption of AI while being confident about preventing any potential misuse. This article summarizes the considerations that must be applied when creating an AI adoption strategy while anticipating and overcoming the unexpected gotchas in a fairly- sized enterprise. 

##### Table of Contents  
- [Common AI uses](#common-ai-uses)
- [The conflicting reality](#the-conflicting-reality)
- [The main stakeholders](#the-main-stakeholders)
- [The basic principles (or rules)](#the-basic-principles-or-rules)
    - [Data governance](#data-governance)
    - [App lifecycle](#app-lifecycle)
    - [AI governance](#ai-governance)
- [The core components](#the-core-components)
    - [Organization data](#organization-data)
    - [AI project hub](#ai-project-hub)
    - [AI gateway](#ai-gateway)
- [The full architecture](#the-full-architecture)

## Common AI uses
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
        BIZResponsibility_@{ shape: "rect", label: "AI suggestions to change any system of record app data are always vetted by this person, who remains accountable for converting the suggestion into actions or data updates." }
    end;

    BizUser & BIZDesc ~~~ BIZExpectation & BIZResponsibility

    classDef User_BIZ stroke:Pink, fill:Pink, font-family:Arial, color:Black, font-weight:Bold
    </code></pre></td>
  </tr>
  <tr>
    <td><pre lang="mermaid"><code>flowchart
    DATAUser([Data steward])
    class DATAUser User_DATA
    DATADesc@{ shape: "text", label: "The data analysts for the data sources spread across system of record apps. They could be either from business or from IT functions." }
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
    DADMDesc@{ shape: "text", label: "The data administrator controls the data that is directly queried/ exposed for consumption by an AI application." }
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
    COEDesc@{ shape: "text", label: "The team that is responsible to craft and maintain the company's AI Adoption strategy. They also monitor value realization from past projects and update best practices based on that. This team is made of representatives from IT, Legal, Business, Cybersecurity, Risk & Compliance etc." }
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
    SoRADMUser([SoR administrator])
    class SoRADMUser User_SoRADM
    SoRADMDesc@{ shape: "text", label: "The administrator (typically, in the IT function) of the business apps used directly by business users to track activities inside the company." }
    subgraph SoRADMExpectation["What the stakeholder expects"]
        SoRADMExpectation_@{ shape: "rect", label: "User-level access controls configured in the app are respected even when the data leaves the system." }
    end;
    subgraph SoRADMResponsibility["What is expected of the stakeholder"]
        SoRADMResponsibility_@{ shape: "rect", label: "Provide inputs for which data can be accessed by which user/ role." }
    end;

    SoRADMUser & SoRADMDesc ~~~ SoRADMExpectation & SoRADMResponsibility

    classDef User_SoRADM stroke:Magenta, fill:Magenta, color: White, font-family:Arial, font-weight:Bold
    </code></pre></td>
  </tr>
</table>

## The basic principles (or rules)

Let us enlist the simplest principles here which will drive how the AI adoption strategy will be eventually articulated. You may wish to evaluate the applicability of each of these principles to your organization and thereby craft a bespoke strategy for your own use. A degree of healthy skepticism is a good thing when an organization is considering building a strategy around the use of AI. Quite a few examples of autonomous agents have been seen to actively pursue creative means to bypass the governance limits imposed on traditional systems. Simply put, AI is a new beast and even its creators are advocating for vigilance when using it. There is no reason therefore for an organization to put its guard down, which is why the principles outlined below should be periodically reviewed and honed for use over time.

### Data governance
* **Data- gateway**. It is difficult to manage a large number of AI apps having access to multiple scattered applications in a fragmented landscape, so a managed centralized data channel is preferable. It either pulls such data from the original systems on- demand or keeps the data replicated internally at an acceptable periodic cadence. Some other benefits that follow from this approach are,
    - Similar SoR applications may be consolidated into a single [star-schema concept](https://en.wikipedia.org/wiki/Star_schema) which is universally understood by the organization. Transformations used to achieve this can be re-used multiple times instead of each app being concerned about it when interacting with individual apps
    - Many modern SaaS applications place limitations on the number of direct (Api/ OData) calls to query data. Such limitations may be bypassed by actually replicating the data inside the data- gateway.
    - Older applications may lack the esssential security infrastructure that inspires confidence when exposing them to AI
* **At- rest data access control**. Requests for data made to the gateway are served only if the access to the requestor is also granted to the original data source, thus user access controls in the original data sources are replicated at the gateway. 
* **Privacy**. A data- gateway is required to maintain the same classification of data sensitivity as the original application. The organization maintains certain data points to be sensitive to its business and requires that sensitive data like this are omitted or redacted when interacting with AI apps communicating with external LLMs. 
* **User due diligence**. Users that have access to the managed SoR apps could directly extract data from those apps and dump them into data files (say JSONs, CSVs etc.) and then feed the data into AI apps, thus inadvertently disclosing potentially sensitive data. Such practices should be actively discouraged by monitoring calls to external AI LLMs or by other stricter controls. 
* **Standard pre-built AI**. Elevating publicly available data warehouses or analytical platform products to become data- gateway often comes with the dual advantages of 
    - ability to quickly create data synchronization flows using standard connectors from other systems, 
    - and ready- to- use AI capabilities in these products that can allow users (and apps) to run natural language queries, without the need of extracting the data and then process it through a separate AI app. Some examples include [Cortex AI](https://www.snowflake.com/en/product/features/cortex/) in [SnowFlake](https://www.snowflake.com/en/) and [Copilot](https://learn.microsoft.com/en-us/fabric/fundamentals/copilot-fabric-overview) in [Microsoft Fabric](https://www.microsoft.com/en-us/microsoft-fabric).
* **Unified data catalog** A centralized data- gateway also maintains the meta-data or the catalog for the data contained in it, so potential users can clearly see the exact data points that they need access to, and may place access requests in the source SoR systems accordingly.
* **Avoid license multiplexing**. Some vendors like [Microsoft](https://www.microsoft.com/en-us/licensing/product-licensing/power-platform) may place restrictions on use of data by user accounts lacking appropriate licenses when the data has been extracted from the SoR apps in a non- standard way. This may impact how the data- gateway is designed. Check this with your vendor.

### App lifecycle
* **Approvals necessary**. To prevent unwanted data leakages about internal processes or data, it is important to know which apps share what data to _external_ LLMs. In case such interaction benefits the organization, the AI-CoE should approve formal requests from the app, stating the type of data shared outside.
* **In- transit data access control**. Data is sacred to an organization and the same level of users access applied to data residing in the original systems are respected when the user wants an AI agent to process this data on his or her behalf. 
* **Human in the loop**. All updates and actions performed by the app MUST be approved by the business user. The user is still held accountable for the outcome of the app use. In fact, all updates that are made to the SoR apps must be made using the user's own credential so that the audit logs native to the SoR app show up the records modified as the user. 
* **Active feedback**. The user of the app should always be able to clearly identify if data shown is AI- generated. A mechanism for the user to provide feedback on the quality of the AI suggestion may be made available in the app. Automated feedback may also be registered by checking _how much_ of the AI suggestion was accepted _verbatim_ by the user.
* **No direct SoR update**. Apps must not bypass the business validation logic already present in the SoR when updating data inside it. In other words, citizen developers should create apps that interact with SoRs using _standard_ user interface or Apis in the respective SoR, and not create apps native to the SoR that can potentially update the underlying database directly. Apps native to specific SoRs can be vibe- coded too and typically require deployment to the SoR. Such apps are out of the scope here and must follow the usual route of IT approvals.
* **LLM or not**. Natural language models are actually a subset of what AI covers. Standard AI services dedicated for common tasks like language translations, image and speech recognition, text extraction, etc. are often cheaper and more accurate than issuing LLM prompts to achieve similar results.
* **App support**. Since the apps are created often by business users, some of them _acting_ as citizen developers, the business should also responsible for maintaining the apps in the future. AI-CoE may facilitate this process by providing a common source control repository destination to hold the source code.
* **App usage**. The AI-CoE publishes a dashboard of the app usage to be consumed by the owning business teams so that either the app is improved to make it more appealing or it is inactivated to prevent further organization expense. Active monitoring becomes especially relevant as there are [studies](https://medium.com/@Fransantolo/95-of-corporate-generative-ai-projects-fail-mit-study-finds-47ad5d50db32) that show that AI apps look great during demos, but lose their charm over time. Here are some examples of the data that should be available from the dashboard,
    - [Invocations] Number of times app has been invoked in a month
    - [Universality] Number of _different_ users that have used the app in a month
    - [Value] How much value is it providing to the business users. Do users often have to dramatically alter the suggestions made by the AI app?
    - [Cost] How much is the app costing the organization in terms of token or AI credit usage?
* **App library**. All apps made by citizen developers should be placed in a public collection and each of them described in a business- readable language to encourage others to
    - Be inspired of how such apps followed the best practices laid out by the AI-CoE (real - life examples)
    - Avoid re-inventing the wheel by creating yet another app to cater to the same requirements as an older app created by someone else, instead of improving it

### AI governance
* **Legal requirements**. The countries in which organizations operate may be subject to specific local regulatory requirements (like the [EU AI act](https://artificialintelligenceact.eu/)). This is why input from the legal team is crucial when AI-CoE formulates policies.
* **AI- gateway**. All LLM calls (especially to external Apis) may only go via an AI- gateway, maintained by the AI-CoE, that applies many governance principles uniformly. Since the AI adoption is expected to quickly gain volume when the gates are opened, it is highly recommended to have these principles applied in a fashion that minimizes human interactions.
* **Throttling token usage**. There may be a need to "budget" token or AI credit usage base on the app or the department that consumes it, as some apps may provide mowants to re business value than others. 
* **Data redaction**. Policies related to preventing or ambiguating sensitive data before it leaves the premises can be effectively enforced through this AI- gateway based on the data classifications maintained in the data- gateway.
* **Logging**. LLM calls are tracked universally for the following data on which the **App Usage** dashboard is created.
    - incurred cost of the call so that it can be attributed to the app or to the organization using the app, 
    - data shared and received, 
    - and perhaps, most importantly for capturing the user's perspective on the quality of the AI suggestion.
* **Internal LLM**. If an organization is concerned about token costs, sensitivity of the data that the LLM processes, or using overly complicated apps for simple AI tasks, an internal LLM stationed on premises is a great alternative to using online vendor- provided LLM alternatives.

## The core components
The core components in an AI adoption strategy may then be classified into the following groups.

### Organization data
Organization data can be classified into 3 categories
1. **Managed SoR apps**. Managed system of record (SoR) apps like ERP, CRM, pricing systems etc. These are usually structured into relational data and such systems are usually maintained by the IT.
1. **Unstructured**. There could be files shares having unstructured data like data lakes or file shares.
1. **Unmanaged**. This category refers to data handled by indivudual users, like private mailboxes, private dumps of data taken from either of the other 2 categories. We rely solely on user discretion to not share such data to external parties. As a result they are the least preferred way of sharing data with AI apps.

All of the data is held behind the data- gateway to prevent direct exposure to AI apps or agents.

``` mermaid
flowchart
    BizUser([Business user])
    class BizUser User_BIZ

    subgraph CompanyData[Organization data]
        subgraph GoldenSystemOfRecord[Data gateway]
            DataStewards(["Data steward"])
            class DataStewards User_DATA
            DataAdmin([Data admin])
            class DataAdmin User_DADM

            DataClassifications@{ shape: cyl, label: "Data classifications" }
            class DataClassifications Database
            DGAccessControl@{ shape: cyl, label: "Access control" }
            class DGAccessControl Database

            DataCatalog@{ shape: doc, label: "Catalog of data exposed" }
            class DataCatalog AiArtifacts

            DataLlmSuite@{ shape: doc, label: "Native generative AI suite<br/> (see under <a href="#data-governance">Standard pre-built AI</a>)" }
            class DataLlmSuite AiArtifacts

            DataAdmin -- configures --> DataClassifications
            DataAdmin -- configures --> DGAccessControl 
            DataStewards -. provides inputs .-> DataClassifications
        end
        style GoldenSystemOfRecord color:blue, font-family:Fantasy, Trebuchet MS
        subgraph Organized["Systems of Record (SoRs)"]
            ERPs@{ shape: h-cyl, label: "ERPs" }
            CRM@{ shape: h-cyl, label: "CRMs" }
            PLM@{ shape: h-cyl, label: "Product Lifecycle Management" }
            HR@{ shape: h-cyl, label: "Human Resources" }
            Procurement@{ shape: h-cyl, label: "Procurement" }
            SupportSystem@{ shape: h-cyl, label: "Business Support" }
            Pricing@{ shape: h-cyl, label: "Pricing" }
            SoRADMUser([SoR administrator])
            class SoRADMUser User_SoRADM
            SoRAccessControl@{ shape: cyl, label: "Access control" }
            class SoRAccessControl Database

            ERPs & CRM & PLM & HR & Procurement & SupportSystem & Pricing ~~~ SoRADMUser & SoRAccessControl

            SoRADMUser -- configures --> SoRAccessControl
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

        DataStewards <-. interfaces .-> SoRADMUser
        Organized -. periodically sync .-> GoldenSystemOfRecord
        Unstructured -. export files on creation/ update .-> GoldenSystemOfRecord
        SoRAccessControl -- dictates --> SnowflakeAccessControl
        DataAdmin -- maintains --> DataCatalog
    end
    style CompanyData stroke:None, fill:#f7e0c6, color:blue, font-family:Fantasy, Trebuchet MS

    AiApp@{ shape: doc, label: "**AI apps/ agents**" }
    class AiApp AiApps

    BizUser -- maintains --> UnmanagedData
    GoldenSystemOfRecord -- fetches data --> AiApp

    classDef User_DATA stroke:Orange, fill:Orange, font-family:Arial, color:Black, font-weight:Bold
    classDef User_DADM stroke:Blue, fill:Blue, color: White, font-family:Arial, font-weight:Bold
    classDef User_SoRADM stroke:Magenta, fill:Magenta, color: White, font-family:Arial, font-weight:Bold
    classDef User_BIZ stroke:Pink, fill:Pink, font-family:Arial, color:Black, font-weight:Bold
    classDef AiArtifacts stroke: Black, fill: Red, color: White, font-family: Arial, font-weight: bold, text-align:justify, text-justify:inter-word
    classDef AiApps stroke: Blue, fill: Blue, color: White, font-family: Arial, font-weight: bold, text-align:justify, text-justify:inter-word
    classDef Database stroke: Brown, stroke-width: 3px, text-align:justify, text-justify:inter-word
```

### AI project hub
The project hub is the collection of all apps and agents built by the citizen developer and addressing the different types of [use cases](#common-ai-uses) as explained previously. Having these collected in a single repository helps in applying the governance uniformly. The following diagram describes
- the interactions of the business users and citizen developers, and
- the artifacts in the public domain that inspire developers to create new apps and improve existing ones.
``` mermaid
flowchart
    CitizenDev([Citizen developer])
    class CitizenDev User_CTZ
    BizUser([Business user])
    class BizUser User_BIZ
    CoE([AI-CoE])
    class CoE User_COE

    subgraph AIProject[AI Project hub]
        subgraph Apps[AI apps/ agents]
            VibeCodedApp@{ shape: doc, label: "**Vibe- coded app**" }
            class VibeCodedApp AiApps
            LLMProj@{ shape: doc, label: "**Generative AI**" }
            class LLMProj AiApps
            Chatbot@{ shape: doc, label: "**Chatbot**" }
            class Chatbot AiApps
        end;
        style Apps color:blue, font-family:Fantasy, Trebuchet MS
        AppCatalog@{ shape: doc, label: "Catalog of projects, illustrations of how best practices have been applied." }
        class AppCatalog AiArtifacts
        AppMetrics@{ shape: doc, label: "Dashboard of usage of apps and user confidence in it, based on evals being logged." }
        class AppMetrics AiArtifacts
        SourceControl@{ shape: cyl, label: "Source control for apps" }
        class SourceControl Database
        BestPractices@{ shape: doc, label: "Best practices for AI projects, architecture, etc." }
        class BestPractices AiArtifacts

        AppCatalog -. references .-> BestPractices
        Apps -- saves to --> SourceControl
    end;
    style AIProject stroke:None, fill:#ebfcfc, color:blue, font-family:Fantasy, Trebuchet MS

    CitizenDev -. references .-> BestPractices 
    CitizenDev -- references & enriches --> AppCatalog 
    CitizenDev -- collects metrics and continually improves solution --> AppMetrics

    ExternalLLMNeeded@{ shape: diamond, label: "?" }
    CitizenDev -- if app makes direct calls to external LLM during runtime, approval is needed. Provide the (sensitive) data points to be sent as inputs to the LLM and the justification thereof. --> ExternalLLMNeeded
    ExternalLLMNeeded <-. interacts .-> CoE
    ExternalLLMNeeded -- Approved. Creates application --> Apps

    BizUser -- calls or uses application --> Apps 

    CoE -- maintains and enriches --> BestPractices
    CoE -- maintains --> AppMetrics 
    CoE -- maintains infrastructure of --> SourceControl

    classDef AiArtifacts stroke: Black, fill: Red, color: White, font-family: Arial, font-weight: bold, text-align:justify, text-justify:inter-word
    classDef AiApps stroke: Blue, fill: Blue, color: White, font-family: Arial, font-weight: bold, text-align:justify, text-justify:inter-word
    classDef Database stroke: Brown, stroke-width: 3px, text-align:justify, text-justify:inter-word
    classDef User_CTZ stroke:LightBlue, fill:LightBlue, font-family:Arial, color:Black, font-weight:Bold
    classDef User_BIZ stroke:Pink, fill:Pink, font-family:Arial, color:Black, font-weight:Bold
    classDef User_COE stroke:Black, fill:Black, color: White, font-family:Arial, font-weight:Bold
```

### AI gateway
The apps or agents using generative AI require to be managed to control the data churned by the external models and also the expense incurred out of token usage. In addition, all calls are to be logged so the interactions can be audited. Such logs can also function as a test bed for future improvements to the apps.
``` mermaid
flowchart
    BizUser([Business user])
    class BizUser User_BIZ
    CoE([AI-CoE])
    class CoE User_COE

    subgraph AIGateway[AI gateway]
        TokenGovernance@{ shape: cyl, label: "Token/ AI credits governance" }
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
        subgraph Models["AI Models"]
            ExternalModel@{ shape: braces, label: "External LLMs<br/>Claude, Copilot, ChatGPT etc."}
            InternalModel@{ shape: doc, label: "Internal LLM" }  
            class InternalModel AiArtifacts
        end
        style Models stroke:None, fill:#c7fcd6, color:blue, font-family:Fantasy, Trebuchet MS

        ExternalLLMApproved -- Yes. Token use within limits? --> TokenUseApproved -. references .-> TokenGovernance 
        ExternalLLMApproved -- No --> MakeCall
        TokenUseApproved -- Yes --> MakeCall
        ExternalLLMApproved -. references .-> ApprovalsForExternalLlms
        PlaceCall <-. interacts .-> Models
        RedactData -. references .-> RedactPolicies
        GathersUserFeedback -- saves eval --> CallLogAsEvals
    end
    style AIGateway stroke:None, fill:#f8ebfa, color:blue, font-family:Fantasy, Trebuchet MS

    LLMProj@{ shape: doc, label: "**Generative AI**" }
    class LLMProj AiApps
    LLMProj -- External LLM needed? --> ExternalLLMApproved

    BizUser ~~~ CoE

    CoE -- configures --> TokenGovernance
    CoE -- configures --> ApprovalsForExternalLlms
    CoE -- maintains --> InternalModel
    CoE -- routinely checks for low user satisfaction and facilitates app improvement or retirement --> CallLogAsEvals

    BizUser -. gives feedback for the AI suggestion .-> GathersUserFeedback

    classDef AiArtifacts stroke: Black, fill: Red, color: White, font-family: Arial, font-weight: bold, text-align:justify, text-justify:inter-word
    classDef AiApps stroke: Blue, fill: Blue, color: White, font-family: Arial, font-weight: bold, text-align:justify, text-justify:inter-word
    classDef Action stroke:None, fill: #f6f0f7, color:blue, font-family:Tahoma, text-align:justify, text-justify:inter-word
    classDef Database stroke: Brown, stroke-width: 3px, text-align:justify, text-justify:inter-word
    classDef User_COE stroke:Black, fill:Black, color: White, font-family:Arial, font-weight:Bold
    classDef User_BIZ stroke:Pink, fill:Pink, font-family:Arial, color:Black, font-weight:Bold
```

## The full architecture
Let us combine the stakeholders, the components and the principles dervied together in a unified diagram so that all interactions become visible. The natural next steps is to evaluate your organization readiness for each node and edge in this diagram and there after make a plan of action for the missing parts. 

``` mermaid
flowchart 
    subgraph Legend[**LEGEND**]
        direction TB
        AiArtifact@{ shape: doc, label: "Public knowledge base artifact" }
        class AiArtifact AiArtifacts
        AiApp@{ shape: doc, label: "AI app/ agent. See <a href="#the-most-common-ai-uses">use cases</a>" }
        class AiApp AiApps
        Team(["User/ team"])
        Database@{ shape: cyl, label: "Data participating directly in the AI architecture" }
        class Database Database
        subgraph Component[ ]
            Comp@{ shape: "text", label: "Component or subcomponent" }
        end;
    end;
    style Legend stroke:Black, stroke-width: 5px, fill:None, color:blue, font-family:Fantasy, Trebuchet MS

    CitizenDev([Citizen developer])
    class CitizenDev User_CTZ
    BizUser([Business user])
    class BizUser User_BIZ
    CoE([AI-CoE])
    class CoE User_COE

    subgraph CompanyData[Organization data]
        subgraph GoldenSystemOfRecord[Data gateway]
            DataStewards(["Data steward"])
            class DataStewards User_DATA
            DataAdmin([Data admin])
            class DataAdmin User_DADM

            DataClassifications@{ shape: cyl, label: "Data classifications" }
            class DataClassifications Database
            DGAccessControl@{ shape: cyl, label: "Access control" }
            class DGAccessControl Database

            DataCatalog@{ shape: doc, label: "Catalog of data exposed" }
            class DataCatalog AiArtifacts

            DataLlmSuite@{ shape: doc, label: "Native generative AI suite<br/> (see under <a href="#data-governance">Standard pre-built AI</a>)" }
            class DataLlmSuite AiArtifacts

            DataAdmin -- configures --> DataClassifications
            DataAdmin -- configures --> DGAccessControl 
            DataStewards -. provides inputs .-> DataClassifications
        end
        style GoldenSystemOfRecord color:blue, font-family:Fantasy, Trebuchet MS
        subgraph Organized["Systems of Record (SoRs)"]
            ERPs@{ shape: h-cyl, label: "ERPs" }
            CRM@{ shape: h-cyl, label: "CRMs" }
            PLM@{ shape: h-cyl, label: "Product Lifecycle Management" }
            HR@{ shape: h-cyl, label: "Human Resources" }
            Procurement@{ shape: h-cyl, label: "Procurement" }
            SupportSystem@{ shape: h-cyl, label: "Business Support" }
            Pricing@{ shape: h-cyl, label: "Pricing" }
            SoRADMUser([SoR administrator])
            class SoRADMUser User_SoRADM
            SoRAccessControl@{ shape: cyl, label: "Access control" }
            class SoRAccessControl Database

            ERPs & CRM & PLM & HR & Procurement & SupportSystem & Pricing ~~~ SoRADMUser & SoRAccessControl

            SoRADMUser -- configures --> SoRAccessControl
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

        DataStewards <-. interfaces .-> SoRADMUser
        Organized -. periodically sync .-> GoldenSystemOfRecord
        Unstructured -. export files on creation/ update .-> GoldenSystemOfRecord
        SoRAccessControl -- dictates --> SnowflakeAccessControl
        DataAdmin -- maintains --> DataCatalog
    end
    style CompanyData stroke:None, fill:#f7e0c6, color:blue, font-family:Fantasy, Trebuchet MS

    subgraph AIProject[AI Project hub]
        subgraph Apps[AI apps/ agents]
            VibeCodedApp@{ shape: doc, label: "**Vibe- coded app**" }
            class VibeCodedApp AiApps
            LLMProj@{ shape: doc, label: "**Generative AI**" }
            class LLMProj AiApps
            Chatbot@{ shape: doc, label: "**Chatbot**" }
            class Chatbot AiApps
        end;
        style Apps color:blue, font-family:Fantasy, Trebuchet MS
        AppCatalog@{ shape: doc, label: "Catalog of projects, illustrations of how best practices have been applied." }
        class AppCatalog AiArtifacts
        AppMetrics@{ shape: doc, label: "Dashboard of usage of apps and user confidence in it, based on evals being logged." }
        class AppMetrics AiArtifacts
        MustUpdateManagedApp@{ shape: diamond, label: "?" }
        UpdateApprovedByUser@{ shape: diamond, label: "?" }
        SourceControl@{ shape: cyl, label: "Source control for apps" }
        class SourceControl Database
        BestPractices@{ shape: doc, label: "Best practices for AI projects, architecture, etc." }
        class BestPractices AiArtifacts

        VibeCodedApp & LLMProj -- must update managed App? --> MustUpdateManagedApp -- Business user has approved changes to be made? (Human- in- the- loop) --> UpdateApprovedByUser
        AppCatalog -. references .-> BestPractices
        Apps -- saves to --> SourceControl
    end;
    style AIProject stroke:None, fill:#ebfcfc, color:blue, font-family:Fantasy, Trebuchet MS

    subgraph AIGateway[AI gateway]
        TokenGovernance@{ shape: cyl, label: "Token/ AI credits governance" }
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
        subgraph Models["AI Models"]
            ExternalModel@{ shape: braces, label: "External LLMs<br/>Claude, Copilot, ChatGPT etc."}
            InternalModel@{ shape: doc, label: "Internal LLM" }  
            class InternalModel AiArtifacts
        end
        style Models stroke:None, fill:#c7fcd6, color:blue, font-family:Fantasy, Trebuchet MS

        ExternalLLMApproved -- Yes. Token use within limits? --> TokenUseApproved -. references .-> TokenGovernance 
        ExternalLLMApproved -- No --> MakeCall
        TokenUseApproved -- Yes --> MakeCall
        ExternalLLMApproved -. references .-> ApprovalsForExternalLlms
        PlaceCall <-. interacts .-> Models
        RedactData -. references .-> RedactPolicies
        GathersUserFeedback -- saves eval --> CallLogAsEvals
    end
    style AIGateway stroke:None, fill:#f8ebfa, color:blue, font-family:Fantasy, Trebuchet MS

    Legend ~~~ CompanyData 
    BizUser ~~~ CitizenDev

    CitizenDev -. references .-> BestPractices & DataCatalog
    CitizenDev -- references & enriches --> AppCatalog 
    CitizenDev -- collects metrics and continually improves solution --> AppMetrics

    ExternalLLMNeeded@{ shape: diamond, label: "?" }
    CitizenDev -- if app makes direct calls to external LLM during runtime, approval is needed. Provide the (sensitive) data points to be sent as inputs to the LLM and the justification thereof. --> ExternalLLMNeeded
    ExternalLLMNeeded <-. interacts .-> CoE
    ExternalLLMNeeded -- Approved. Creates application --> Apps

    GoldenSystemOfRecord -- securely provides data based on the app user's credential --> AIProject
    DataClassifications -- dictates --> RedactPolicies
    SoRAccessControl -- dictates --> DGAccessControl
    UnmanagedData -- <b>RISKY! NOT IT SUPPORTED.</b> --> LLMProj
    DataLlmSuite <-. interacts, for sensitive data .-> InternalModel

    UpdateApprovedByUser -- yes. Perform update using app user's credentials to support auditability. This part of the app may require review by IT. --> Organized
    UpdateApprovedByUser -. app takes user approval and logs it internally .-> BizUser
    Chatbot -- queries --> DataLlmSuite

    BizUser -- calls or uses application --> Apps 
    BizUser -- maintains --> UnmanagedData
    LLMProj -- <b>RISKY! NOT IT SUPPORTED.</b> --> ExternalModel
    GoldenSystemOfRecord -. incremental updates to keep internal LLM in sync .-> InternalModel
    LLMProj -- Yes. External LLM needed? --> ExternalLLMApproved
    AppMetrics -. pulls data from .-> CallLogAsEvals

    BizUser -. gives feedback for the AI suggestion .-> GathersUserFeedback

    CoE -- configures --> TokenGovernance
    CoE -- configures --> ApprovalsForExternalLlms
    CoE -- maintains --> InternalModel
    CoE -- maintains and enriches --> BestPractices
    CoE -- routinely checks for low user satisfaction and facilitates app improvement or retirement --> CallLogAsEvals
    CoE -- maintains --> AppMetrics 
    CoE -- maintains infrastructure of --> SourceControl

    classDef User_CTZ stroke:LightBlue, fill:LightBlue, font-family:Arial, color:Black, font-weight:Bold
    classDef User_BIZ stroke:Pink, fill:Pink, font-family:Arial, color:Black, font-weight:Bold
    classDef User_DATA stroke:Orange, fill:Orange, font-family:Arial, color:Black, font-weight:Bold
    classDef User_COE stroke:Black, fill:Black, color: White, font-family:Arial, font-weight:Bold
    classDef User_DADM stroke:Blue, fill:Blue, color: White, font-family:Arial, font-weight:Bold
    classDef User_SoRADM stroke:Magenta, fill:Magenta, color: White, font-family:Arial, font-weight:Bold
    classDef AiArtifacts stroke: Black, fill: Red, color: White, font-family: Arial, font-weight: bold, text-align:justify, text-justify:inter-word
    classDef AiApps stroke: Blue, fill: Blue, color: White, font-family: Arial, font-weight: bold, text-align:justify, text-justify:inter-word
    classDef Action stroke:None, fill: #f6f0f7, color:blue, font-family:Tahoma, text-align:justify, text-justify:inter-word
    classDef SG stroke:None, fill:#ffffe6, color:blue, font-family:Fantasy, Trebuchet MS
    classDef Database stroke: Brown, stroke-width: 3px, text-align:justify, text-justify:inter-word
```



