``` mermaid
flowchart TB
    %%{init: { "flowchart": { "nodeSpacing": 20, "rankSpacing": 30 }}}%%

    subgraph row1[ ]
        direction LR
        subgraph CitizenDeveloper[ ]
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
        end;
        class CitizenDeveloper Cell
        subgraph BusinessUser[ ]
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
        end;
        class BusinessUser Cell
    end;
    class row1 Row

    subgraph row2[ ]
        direction LR
        subgraph DataSteward[ ]
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
        end;
        class DataSteward Cell
        subgraph DataAdmin[ ]
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
        end;
        class DataAdmin Cell
    end;
    class row2 Row

    subgraph row3[ ]
        direction LR
        subgraph CoE[ ]
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
        end;
        class CoE Cell
        subgraph SorAdmin[ ]
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
        end;
        class SorAdmin Cell
    end;
    class row3 Row

    CitizenDeveloper ~~~ BusinessUser
    DataSteward ~~~ DataAdmin
    CoE ~~~ SorAdmin
    row1 ~~~ row2 ~~~ row3

    classDef Row stroke: White, fill: White
    classDef Cell stroke: Black, fill: White
    classDef User_CTZ stroke:LightBlue, fill:LightBlue, font-family:Arial, color:Black, font-weight:Bold
    classDef User_BIZ stroke:Pink, fill:Pink, font-family:Arial, color:Black, font-weight:Bold
    classDef User_DATA stroke:Orange, fill:Orange, font-family:Arial, color:Black, font-weight:Bold
    classDef User_DADM stroke:Blue, fill:Blue, color: White, font-family:Arial, font-weight:Bold
    classDef User_COE stroke:Black, fill:Black, color: White, font-family:Arial, font-weight:Bold
    classDef User_SoRADM stroke:Magenta, fill:Magenta, color: White, font-family:Arial, font-weight:Bold
```
