``` mermaid
flowchart
    CitizenDev(["Citizen developer"])
    class CitizenDev User_CTZ
    CTZDesc@{ shape: "text", label: "The frontline worker who uses AI and creates applications for an individual or a team to increase productivity." }
    subgraph CTZExpectation["What the stakeholder expects"]
        CTZExpectation_@{ shape: "rect", label: "Clear directions to follow so that the app thus created is safe and performs optimally." }
    end;
    subgraph CTZResponsibility["What is expected of the stakeholder"]
        CTZResponsibility_@{ shape: "rect", label: "Creates applications based on best practices outlined by the AI-CoE while taking appropriate approvals whenever required." }
    end;

    CitizenDev & CTZDesc ~~~ CTZExpectation & CTZResponsibility

    classDef User_CTZ stroke:LightBlue, fill:LightBlue, font-family:Arial, color:Black, font-weight:Bold
```
