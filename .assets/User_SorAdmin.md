``` mermaid
flowchart
    SoRADMUser([SoR administrator])
    class SoRADMUser User_SoRADM
    SoRADMDesc@{ shape: "text", label: "The administrator (typically, in the IT function) of the business apps, typically System of Records, used directly by business users to track activities inside the company." }
    subgraph SoRADMExpectation["What the stakeholder expects"]
        SoRADMExpectation_@{ shape: "rect", label: "User-level access controls configured in the app are respected even when the data leaves the system." }
    end;
    subgraph SoRADMResponsibility["What is expected of the stakeholder"]
        SoRADMResponsibility_@{ shape: "rect", label: "Provide inputs for which data can be accessed by which user/ role." }
    end;

    SoRADMUser & SoRADMDesc ~~~ SoRADMExpectation & SoRADMResponsibility

    classDef User_SoRADM stroke:Magenta, fill:Magenta, color: White, font-family:Arial, font-weight:Bold
```