``` mermaid
flowchart
    BizUser([Business user])
    class BizUser User_BIZ
    BIZDesc@{ shape: "text", label: "The business user who is going to use the app created by the citizen developer." }
    subgraph BIZExpectation["What the stakeholder expects"]
        BIZExpectation_@{ shape: "rect", label: "The app is easy to use and works well. In case of obvious inaccuracies in the AI- created suggestions, it is possible to provide (hopefully in-app) feedback to improve it." }
    end;
    subgraph BIZResponsibility["What is expected of the stakeholder"]
        BIZResponsibility_@{ shape: "rect", label: "AI suggestions to change any system of record data are always vetted by this person, who remains accountable for converting the suggestion into actions or data updates." }
    end;

    BizUser & BIZDesc ~~~ BIZExpectation & BIZResponsibility

    classDef User_BIZ stroke:Pink, fill:Pink, font-family:Arial, color:Black, font-weight:Bold
```
