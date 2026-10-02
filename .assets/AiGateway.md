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
        CallLogAsEvals@{ shape: cyl, label: "Call logs with details: app, request, response, token cost, user feedback of AI suggestion" }
        class CallLogAsEvals Database
        subgraph MakeCall[Query LLM]
             RedactData[Redact/ omit sensitive data]
             class RedactData Action
             PlaceCall[Place call]
             GathersUserFeedback[Gathers user feedback, either by asking user or by assessing adoption of the AI suggestion.]
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
