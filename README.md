
# Creating an AI adoption strategy for an enterprise
Artificial intelligence has already proven itself quite impactful in the way organizations operate today. Unlike prior technological advances, its **easy adoption**, **short time- to- value realization** and **versatility of application** are paving the way for citizen developers to create useful applications themselves. This empowers the business users who now automate workflows, easily add functionality atop their favorite applications, get targeted queries answered across multiple datasets almost instantaneously and on their own without the need for a traditional IT function. On one hand, this brings in flexibility and speed to the activities inside an organization, but on the other hand, it raises the risk of unmanaged data leaks and excessive expenses incurred because of unfettered usage.

The focus therefore shifts towards "managing" this innovation and productivity boom so that an organization can encourage greater adoption of AI while being confident about preventing any potential misuse. The rest of the article here summarizes the considerations that must be applied when creating an AI adoption strategy while anticipating and overcoming the unexpected gotchas in a large enterprise. 

##### Table of Contents  
- [The most common AI uses](#the-most-common-ai-uses)
- [The conflicting reality](#the-conflicting-reality)
- [The basic principles](#the-basic-principles)
    - [The main stakeholders](#the-main-stakeholders)
    - [The core components](#the-core-components)
- [A proposal](#a-proposal)

## The most common AI uses
Artificial intelligence is advancing at an ever- accelerating pace and break- through innovations in their capability are almost a staple of everyday news headlines. However if we consider the most rudimentary uses for AI, only a few distinct categories emerge. Note that real- world AI applications may often fall into more than one category mentioned here. 

| Category | Author | Purpose | Example | Included in the AI adoption strategy |
| -- | -- | -- | -- | -- |
| **Vibe- coded app** | Citizen developer | Business users often require their everyday work applications to behave in a more intuitive way and favor greater automation for the labor-intensive part of such interactions. They build apps often with bespoke user interfaces that favor productivity. AI is used to create the app but AI is not used inside the app.  | The procurement manager wishes to auto-approve a large inflow of low- value purchase orders to specific pre-approved vendors, thus saving a considerable amount of time. | ✅ |
| **Generative AI** | Citizen developer | Users want to bring generative AI capabilities to their daily work by getting them triggered autonomously within the applications that they normally use or by an AI agent that makes helpful suggestions. | The warehouse receiving clerk receives daily emails from vendors informing the company of the schedule and size of the shipments they are making in the coming weeks. The clert plans the warehouse space and workers in advance based on this information. She creates an agent that reads the inbox and makes a daily summary against each purchase order being received that is used to post advanced shipment notices to the ERP. | ✅ |
| **Chatbot** | Citizen developer | Users raise questions in natural language to gain insights into data that would otherwise be hard to analyze, possibly because the data is spread in disconnected data sets. Chatbots may be created unique to a functional domain or even a sub-team inside it, based on the data they need access to. | An order desk employee needs to answer a call from a customer regarding the progress of a customer order that can be gleaned from a CRM system in which the order is booked, an ERP system which tracks the execution of manufactured units and a transportation management system to track shipping status. She has access to these systems to the extent needed to track progress of orders. | ✅ |
| **Pre- built** | Vendor | Applications being used by business users already have standard AI functionality embedded inside. These are typically outside the ambit of a company's AI adoption strategy because the interaction with the LLMs happens natively inside the application and often cannot be intercepted. Vendors usually provide an assurance of data privacy as part of their customer service agreement. | A product life cycle management system contains functionality to identify closely resembling products based on standard attributes like bill of materials, variants like colors & shapes, technical specifications etc. The feature is used to remove duplicates and keep the product catalog lean. The admin needs to simply flip a switch to enable the functionality before use. | ❌ |
| **Custom data model** | Data analysts | Applications built to use AI in a non-natural language based context, usually by creating models from scratch based on customized and private data sets to yield predictions or forecasts. As this is often done by data analysts in the IT function who are expected to be fluent with AI, safeguards are assumed to have been placed already. | A company needs to set its yearly sales targets for the coming period. It analyzes its annual sales data for its flagship products, according to a particular machine learning algorithm, that looks at narrow behavioral traits of its niche customer base. | ❌ |


## The conflicting reality
As may be seen from the use cases above, deriving the true value from AI requires it to first assimilate facts from a wide range of data sources as well as sufficiently large samples of data in those sources, eventually yielding results that are holistic in nature. But if an organization has not yet created an AI adoption strategy, it is likely that they are yet to strike the right balance between conflicting forces that push them to either adopt AI or exercise caution against it. 

``` mermaid
kanban
    Pros[<h3>Factors favoring AI adoption</h3>]
        [<span style="font-size:xx-large">👑</span><p>Leadership push</p>]
        [<span style="font-size:xx-large">🧑‍💻</span><p>Enthusiastic citizen developers</p>]
    Cons[<h3>Factors warranting caution</h3>]
        [<span style="font-size:xx-large">🗗</span><p>Heterogenous application landscape</p>]
        [<span style="font-size:xx-large">⁉️</span><p>Unprepared for governance</p>]
```

* **Leadership push**. The senior management are coerced by their shareholders to demonstrate "competitiveness" or adopt a more "tech- embracing attitude" with respect to their peers. 
* **Enthusiastic citizen developers**. Frontline workers in the business have had a positive experience with AI and are raring to create or use even more tools to enhance their productivity. 
* **Heterogenous application landscape**. There may be too many, and often duplicate, discrete systems that information lives in. Also, not all of them may be in the same state of readiness to safely extract data from.
* **Unprepared for governance**. The IT function has reservations against unbridled use of tokens or leakage of sensitive company data (often intellectual property) to external models or even to unauthorized internal employees. Without sufficient guardrails, they may resist AI exposure.

## The basic principles
* data governance
* token usage
* check deck
* feedback loop ensuring continuous value delivery, at least initially
* auditability and accountability
* AI is a new beast- even the leaders appear unsure- so, no assumptions!

### The main stakeholders

<table>
  <tr>
    <td><pre lang="mermaid"><code>flowchart
    CitizenDev(["<b>Citizen developer</b>"])
    class CitizenDev User_CTZ
    CTZDesc@{ shape: "text", label: "The frontline worker who creates applications for individual or team use to increase productivity." }
    subgraph CTZExpectation["<b>What the stakeholder expects</b>"]
        CTZExpectation_@{ shape: "rect", label: "Clear directions for the developer to follow so that the app thus created is safe, performs optimally and helps to boost productivity." }
    end;
    subgraph CTZResponsibility["<b>What is expected of stakeholder</b>"]
        CTZResponsibility_@{ shape: "rect", label: "Create applications based on outlined best practices while taking appropriate approvals whenever required." }
    end;
    CitizenDev & CTZDesc ~~~ CTZExpectation & CTZResponsibility

    classDef User_CTZ stroke:LightBlue, fill:LightBlue, font-family:Arial, color:Black
    </code></pre></td>
    <td><pre lang="mermaid"><code>flowchart
    BizUser([<b>Business user</b>])
    class BizUser User_BIZ
    BIZDesc@{ shape: "text", label: "The business user who is going to use the app. This user is different than the citizen developer for apps created for a group of people." }
    subgraph BIZExpectation["<b>What the stakeholder expects</b>"]
        BIZExpectation_@{ shape: "rect", label: "The app is easy to use and works well. In case of obvious inaccuracies, feedback may be provided to the app creator for improving it." }
    end;
    BIZResponsibility["<b>What is expected of stakeholder</b>"]
        BIZResponsibility_@{ shape: "rect", label: "Recommendations from the AI application, if applicable, are always vetted by this person before any updates in the line of business apps." }
    end;
    BizUser & BIZDesc ~~~ BIZExpectation & BIZResponsibility

    classDef User_BIZ stroke:Pink, fill:Pink, font-family:Arial, color:Black
    </code></pre></td>
  </tr>
  <tr>
    <td><pre lang="mermaid"><code>flowchart
    DATAUser([<b>Data steward</b>])
    class DATAUser User_DATA
    DATADesc@{ shape: "text", label: "The data analysts for the data sources spread across line of business apps." }
    DATAExpectation["<b>What the stakeholder expects</b>"]
        DATAExpectation_@{ shape: "rect", label: "Data classifications are adhered to when interacting with AI systems. Sensitive data never get leaked outside." }
    end;
    DATAResponsibility["<b>What is expected of stakeholder</b>"]
        DATAResponsibility_@{ shape: "rect", label: "Understands the underlying data and provides input for classifying it into the right categories" }
    end;
    DATAUser & DATADesc ~~~ DATAExpectation & DATAResponsibility

    classDef User_DATA stroke:Orange, fill:Orange, font-family:Arial, color:Black
    </code></pre></td>
    <td><pre lang="mermaid"><code>flowchart
    DADMUser([<b>Data administrator</b>])
    class DADMUser User_DADM
    DADMDesc@{ shape: "text", label: "The data administrator sources directly exposed for consumption by an AI application." }
    DADMExpectation["<b>What the stakeholder expects</b>"]
        DADMExpectation_@{ shape: "rect", label: "Following the best practices sufficiently safeguards the data from misuse by the AI app." }
    end;
    DADMResponsibility["<b>What is expected of stakeholder</b>"]
        DADMResponsibility_@{ shape: "rect", label: "Data is classified correctly and data access governance for individuals or service accounts follow the usual governance." }
    end;
    DADMUser & DADMDesc ~~~ DADMExpectation & DADMResponsibility

    classDef User_DADM stroke:Blue, fill:Blue, color: White, font-family:Arial
    </code></pre></td>
  </tr>
  <tr>
    <td><pre lang="mermaid"><code>flowchart
    COEUser([<b>AI-CoE</b>])
    class COEUser User_COE
    COEDesc@{ shape: "text", label: "The team of people who together hold the responsibility of crafting and maintaining the company's AI Adoption strategy." }
    COEExpectation["<b>What the stakeholder expects</b>"]
        COEExpectation_@{ shape: "rect", label: "Following the best practices sufficiently safeguards the data from misuse by the AI app." }
    end;
    COEResponsibility["<b>What is expected of stakeholder</b>"]
        COEResponsibility_@{ shape: "rect", label: "Data is classified correctly and data access governance for individuals or service accounts follow the usual governance." }
    end;
    COEUser & COEDesc ~~~ COEExpectation & COEResponsibility

    classDef User_COE stroke:Black, fill:Black, color: White, font-family:Arial
    </code></pre></td>
    <td><pre lang="mermaid"><code>flowchart
    LoBADMUser([<b>LoB administrator</b>])
    class LoBADMUser User_LoBADM
    LoBADMDesc@{ shape: "text", label: "The administrator of the business apps used directly by business users to track activities inside the company." }
    LoBADMExpectation["<b>What the stakeholder expects</b>"]
        LoBADMExpectation_@{ shape: "rect", label: "User-level access controls configured in the app are respected even when the data leaves the system." }
    end;
    LoBADMResponsibility["<b>What is expected of stakeholder</b>"]
        LoBADMResponsibility_@{ shape: "rect", label: "Provide inputs for which data can be accessed by which user / role." }
    end;
    LoBADMUser & LoBADMDesc ~~~ LoBADMExpectation & LoBADMResponsibility

    classDef User_LoBADM stroke:Magenta, fill:Magenta, color: White, font-family:Arial
    </code></pre></td>
  </tr>
</table>

### The core components


## A proposal

### Interactions between the components

### The full picture

``` mermaid
 graph LR;
 A[Wiki supports Mermaid] --> B[Visit <a href="https://mermaidjs.github.io">https://mermaidjs.github.io</a> for Mermaid syntax];
```

## Raw
Inputs to AI architecture

EU AI Act

Token usage includes AI tool credits like Copilot credits (check SKU first)


Internal LLM: token conscious, sensitiveity of external LLMs gaining knowledge, not to use overly complicated apps for simple tasks

Token usage should be part of the telemetry just so that the budget controls can be implemented at the line of business level.

Multiplexing requires user license to be granted to the managed app, when updating it. Most vendors are okay to not require licenses if the "right" channels are used to push the data out of the system.

Why create a data gateway?
- The reasoning for data gateway is simplicity of maintainance, access definitions & transformation consolidation. This should not prevent apps from direct access to the individual managed apps, IF that requirement is felt.
- Consolidation of different data sources
- Unified way to give access- One security gate.
- Avoid expensive API throttled direct connections to the managed apps
- Older applications may not have modern safety nets to make point to point solutions
- if multiple systems (of ERP, say) exist, citizen developers tend to make managed app- specific applications.

IT must approve updates to managed applications because
- native validation logic must not be bypassed
- updates might require additional approvals in a matrixed organization

QUESTION
What considerations favor the creation of an Internal on-premises LLM?
How can the low code platform ensure that an app is not created at a too low level on the System of record.
Talk to Vinod about how user access control is enforced.





