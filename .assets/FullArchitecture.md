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
        SoRAccessControl -- dictates --> DGAccessControl
        Unstructured -. export files on creation/ update .-> GoldenSystemOfRecord
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
        CallLogAsEvals@{ shape: cyl, label: "Call logs with details: <ol><li>. request</li><li>. response</li><li>. token cost</li><li>. user acceptance of AI suggestion</li></ol>" }
        class CallLogAsEvals Database
        subgraph MakeCall[Query LLM]
             RedactData[Redact/ omit sensitive data]
             class RedactData Action
             PlaceCall[Place call]
             GathersUserFeedback[Gathers user feedback, <ul><li>. by detecting extent to which user adopts suggestion,</li><li>. or, by explicitly asking user in the app.</li></ul>]
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
        GathersUserFeedback -- saves AI eval --> CallLogAsEvals
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
