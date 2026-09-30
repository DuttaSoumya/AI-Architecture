``` mermaid
flowchart
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
```