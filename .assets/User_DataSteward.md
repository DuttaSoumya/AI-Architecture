``` mermaid
flowchart
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
```