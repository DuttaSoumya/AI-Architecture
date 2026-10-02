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
        SoRAccessControl -- dictates --> DGAccessControl
        DataAdmin -- maintains --> DataCatalog
    end
    style CompanyData stroke:None, fill:#f7e0c6, color:blue, font-family:Fantasy, Trebuchet MS

    AiApp@{ shape: doc, label: "**AI apps/ agents**" }
    class AiApp AiApps

    BizUser -- maintains --> UnmanagedData
    GoldenSystemOfRecord -- fetch data --> AiApp
    UnmanagedData -- <b>RISKY! NOT IT SUPPORTED.</b> --> AiApp

    classDef User_DATA stroke:Orange, fill:Orange, font-family:Arial, color:Black, font-weight:Bold
    classDef User_DADM stroke:Blue, fill:Blue, color: White, font-family:Arial, font-weight:Bold
    classDef User_SoRADM stroke:Magenta, fill:Magenta, color: White, font-family:Arial, font-weight:Bold
    classDef User_BIZ stroke:Pink, fill:Pink, font-family:Arial, color:Black, font-weight:Bold
    classDef AiArtifacts stroke: Black, fill: Red, color: White, font-family: Arial, font-weight: bold, text-align:justify, text-justify:inter-word
    classDef AiApps stroke: Blue, fill: Blue, color: White, font-family: Arial, font-weight: bold, text-align:justify, text-justify:inter-word
    classDef Database stroke: Brown, stroke-width: 3px, text-align:justify, text-justify:inter-word
```
