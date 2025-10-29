As a data science expert, rigorous **Task Abstraction** and systematic **Validation** are necessary to ensure that visualization and analytical solutions are effective and address the actual business problem. This methodology structures the design process from the high-level domain constraints down to the lowest level of computational efficiency.

### Visualization Design and Validation (14 Marks)

Validation in visualization ensures that the system reliably addresses user needs and avoids fundamental errors at every stage of the design process.

#### I. Task Abstraction Analysis

Task abstraction is the process of transforming domain-specific task descriptions into an abstract form, which allows the designer to reason about the similarities and differences between distinct problems. This framework defines user goals across three levels of action: Analyze (High-Level), Search (Mid-Level), and Query (Low-Level).

##### 1. High-Level Actions: Analyze

At the highest level, users use the visualization (vis) either to **Consume** existing information or to **Produce** new information.

| Action Type | Sub-Goal | Description | Source |
| :--- | :--- | :--- | :--- |
| **Consume** | Discover | Using the visualization to find new knowledge that was not previously known. | |
| **Consume** | Present | Communicating something specific and already understood to an audience (e.g., in decision-making). | |
| **Consume** | Enjoy | Engaging in casual encounters with the vis driven by curiosity, rather than a pressing need to verify a hypothesis. | |
| **Produce** | Annotate | Adding graphical or textual annotations associated with existing visualization elements. | |
| **Produce** | Record | Saving or capturing visualization elements as persistent artifacts (e.g., screen shots or parameter settings). | |
| **Produce** | Derive | Producing new data elements based on existing data, such as transforming data types or extracting new attributes. | |

##### 2. Mid-Level Actions: Search

All high-level analysis requires the user to search for elements of interest. The search is classified based on whether the identity and location of the target are known.

*   **Lookup:** Finding a known target at a known location.
*   **Locate:** Finding a known target at an unknown location.
*   **Browse:** Searching for characteristics where the exact target identity is not known in advance.
*   **Explore:** Searching when neither the target nor the location is known, often starting from an overview of everything.

##### 3. Low-Level Actions: Query

These goals are applied once a target or set of targets has been found, categorized by scope:

*   **Identify:** Focuses on a single target; returns its characteristics.
*   **Compare:** Focuses on multiple targets. These tasks are typically more difficult and require more sophisticated idioms.
*   **Summarize (Overview):** Focuses on all possible targets. The goal of providing an overview is extremely common in visualization.

#### II. The Four Levels for Validation

Validation must be applied across the entire design stack, checking the choices made from the conceptual domain level down to the algorithmic implementation. Each level has specific threats to validity—fundamental reasons why the wrong choices might have been made.

##### 1. Domain Situation (Top Level)
*   **Definition:** This level considers the specific context, constraints, and requirements of the application domain (e.g., medical data standards in healthcare).
*   **Threat:** **Wrong Problem**. The threat is that the fundamental requirements were misunderstood.
*   **Validation Approach:** Observe and interview target users.

##### 2. What–Why Abstraction Level
*   **Definition:** This level involves mapping domain-specific problems and data into abstract, domain-independent forms, such as abstract data attributes and tasks.
*   **Threat:** **Wrong Task/Data Abstraction**. This means the data types or goals were incorrectly defined in abstract terms.
*   **Validation Approach:** Justify encoding/interaction design decisions.

##### 3. Interaction Idiom (How Level)
*   **Definition:** This concerns the design of the idioms that specify the approach to visual encoding and user interaction (e.g., using a bar chart or the "drag-and-drop" idiom).
*   **Threat:** **Ineffective Encoding/Interaction Idiom**. The chosen visual design or interaction technique is ineffective for the task.
*   **Validation Approach:** Justify encoding/interaction design decisions.

##### 4. Algorithm Level (Bottom Level)
*   **Definition:** This level involves the design and implementation of algorithms needed to computationally instantiate the idioms.
*   **Threat:** **Slow Algorithm**. The implemented code is computationally inefficient.
*   **Validation Approach:** Analyze computational complexity; implement the system and measure system time/memory.

#### III. Validation Threats Diagram

The four levels of validation define the hierarchy of potential threats in the visualization design process:

```ascii
+--------------------------+
| 1. Domain Situation      | <-- Threat: Wrong Problem
+--------------------------+
            |
            V
+--------------------------+
| 2. What-Why Abstraction  | <-- Threat: Wrong Task/Data Abstraction
+--------------------------+
            |
            V
+--------------------------+
| 3. Interaction Idiom (How)| <-- Threat: Ineffective Encoding/Idiom
+--------------------------+
            |
            V
+--------------------------+
| 4. Algorithm             | <-- Threat: Slow Algorithm
+--------------------------+
```
