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
