``` mermaid
flowchart
    COEUser([AI-CoE])
    class COEUser User_COE
    COEDesc@{ shape: "text", label: "The team that is responsible to craft and maintain the company's AI Adoption strategy. They also monitor value realization from past projects and accordingly update best practices. This team is made of representatives from IT, Legal, Business, Cybersecurity, Risk & Compliance etc." }
    subgraph COEExpectation["What the stakeholder expects"]
        COEExpectation_@{ shape: "rect", label: "The senior leadership supports the adoption of the governance approach proposed by the AI-CoE." }
    end;
    subgraph COEResponsibility["What is expected of stakeholder"]
        COEResponsibility_@{ shape: "rect", label: "Formulate org- wide policies and build safeguards to use AI in a safe and efficient manner." }
    end;

    COEUser & COEDesc ~~~ COEExpectation & COEResponsibility

    classDef User_COE stroke:Black, fill:Black, color: White, font-family:Arial, font-weight:Bold
```