## Distributed Operating Systems – Unit I & II (Exam Answers)

---

## UNIT–I

---

### 1(a) Explain the different architectures of distributed systems.

A **distributed system architecture** defines how multiple computers (nodes) are organized, how they communicate, and how resources are accessed and managed. Common architectures include:

#### 1. Client–Server Architecture

- **Idea**:  
  - Some machines act as **servers** (provide services/resources).  
  - Others act as **clients** (request and use services).

- **Structure (conceptual diagram)**:

  ```
  Clients         Network           Servers
  -------        ---------         --------
   C1  ------\                   /------ S1 (File server)
   C2  -------====== Internet ===------- S2 (DB server)
   C3  ------/                   \------ S3 (Print server)
  ```

- **Characteristics**:
  - **Centralized control** of some resources (e.g., file server).
  - Clients can be **thin** (simple interface) or **thick** (more logic).
  - Suitable for **transactional** systems (banking, web apps, etc.).

- **Advantages**:
  - Easier management and security at servers.
  - Data consistency is simpler.

- **Disadvantages**:
  - **Single point of failure** (server).
  - Scalability limits if many clients contact one server.

---

#### 2. Peer-to-Peer (P2P) Architecture

- **Idea**:  
  - Each node (peer) acts as **both client and server**.
  - Peers share resources directly with each other.

- **Structure**:

  ```
  P1  -----  P2
   \         / \
    \       /   \
     P3 -- P4 -- P5
  ```

- **Characteristics**:
  - **Decentralized control**, no permanent central server.
  - Often used for **file sharing**, **blockchain**, etc.

- **Advantages**:
  - High **scalability**.
  - No single point of failure (more robust).

- **Disadvantages**:
  - Harder to manage and ensure **security**.
  - Difficult to guarantee **data consistency**.

---

#### 3. Multi-Tier (N-Tier) Architecture

- **Idea**:  
  - System is split into multiple logical layers: **presentation**, **application (business logic)**, and **data**.

- **Typical 3-tier structure**:

  ```
  [Presentation Tier]    ->  Web browser / GUI
  [Application Tier]     ->  Application server
  [Data Tier]            ->  Database server
  ```

- **Characteristics**:
  - Each tier can run on different machines.
  - Clear separation of concerns.

- **Advantages**:
  - Easy to **maintain** and **upgrade** individual tiers.
  - Better **scalability** by adding more servers per tier.

- **Disadvantages**:
  - More complex configuration.
  - Additional network overhead between tiers.

---

#### 4. Distributed Object / Service-Oriented Architecture (SOA, Microservices)

- **Idea**:  
  - System consists of **loosely coupled services** or **objects** that communicate via defined interfaces (e.g., RPC, REST, gRPC).

- **Structure**:

  ```
  Service A  <---->  Service B  <---->  Service C
     |                             |
   Clients                      Databases
  ```

- **Characteristics**:
  - Functions are packaged as **services**.
  - Each service can be developed, deployed, and scaled independently.

- **Advantages**:
  - High **modularity** and **reusability**.
  - Supports continuous deployment.

- **Disadvantages**:
  - Complex **service discovery** and **orchestration**.
  - More challenging debugging and monitoring.

---

#### 5. Hybrid Architectures

- Many real systems combine multiple styles:
  - Example: **Client–server** front-end with **P2P** storage layer.
  - Example: Microservices internally, but exposed as a simple client–server API.

---

**Conclusion**:  
Distributed system architectures include **client–server**, **peer-to-peer**, **multi-tier**, **service-oriented / microservices**, and **hybrids**. The choice depends on requirements like **scalability**, **fault tolerance**, **management complexity**, and **application domain**.

---

### 1(b) Discuss the major issues in distributed operating systems.

A **Distributed Operating System (DOS)** manages a collection of independent computers and makes them appear to the user as a **single coherent system**. Key issues include:

#### 1. Transparency

- **Goal**: Hide the distributed nature from users and applications.
- **Types**:
  - **Location transparency** – users need not know where a resource is located.
  - **Access transparency** – same operations to access local and remote resources.
  - **Migration transparency** – resources/processes can move without affecting users.
  - **Replication transparency** – multiple copies of resources are hidden from the user.
  - **Concurrency transparency** – multiple users sharing resources without interference.
- **Challenge**: Providing transparency while still maintaining good **performance**.

---

#### 2. Communication and Synchronization

- **Reliable Communication**:
  - Need mechanisms for **message passing** or **remote procedure calls (RPC)**.
  - Must handle **packet loss, delays, and reordering**.
- **Synchronization**:
  - No global clock; must use **logical clocks**, **vector clocks**.
  - Processes need **mutual exclusion** and **coordination**.
- **Issue**: Designing efficient synchronization without central coordinator.

---

#### 3. Naming and Naming Services

- Every resource (files, processes, devices) needs a **unique and meaningful name**.
- **Issues**:
  - **Global namespace** across machines.
  - Mapping human-readable names to actual locations (name resolution).
  - Supporting location transparency while allowing resources to move.

---

#### 4. Consistency and Replication

- **Replication** improves performance and fault tolerance.
- **Issue**: Keeping replicas **consistent** across multiple nodes.
  - **Data consistency models** (e.g., strict, sequential, causal, eventual).
- Trade-off between **consistency, availability, and partition tolerance** (CAP theorem).

---

#### 5. Fault Tolerance and Reliability

- In distributed systems, failures are **common**:
  - Node crashes, network partitions, message loss.
- DOS must:
  - Detect failures (e.g., using **timeouts**, **heartbeat messages**).
  - Recover (e.g., **checkpointing**, **rollback**, **replication**).
  - Provide **fault-tolerant** services (e.g., using redundancy, consensus algorithms).
- Major issue: Achieving **reliable** behavior over unreliable components.

---

#### 6. Security

- **Security challenges**:
  - **Authentication** of users and processes.
  - **Authorization** and **access control** for distributed resources.
  - Ensuring **confidentiality** and **integrity** of data over insecure networks.
- Need **cryptographic protocols**, **secure channels**, **key management**.

---

#### 7. Scalability

- System must work efficiently as the number of:
  - Nodes, users, and resources grows.
- **Issues**:
  - Centralized algorithms do not scale; need decentralized solutions.
  - Avoid bottlenecks (single server, single clock, central directory).
  - Hierarchical and distributed algorithms for naming, routing, etc.

---

#### 8. Heterogeneity

- Machines can differ in:
  - **Hardware**, **OS**, **network protocols**, **data formats**.
- DOS must provide:
  - Common interfaces (e.g., middleware, virtual machines).
  - Data conversion and standard protocols (e.g., TCP/IP).

---

**Conclusion**:  
Major issues in DOS include **transparency, communication, naming, consistency, fault tolerance, security, scalability, and heterogeneity**. Proper handling of these issues is essential to provide a **single-system image** over multiple machines.

---

### 2(a) Describe communication networks used in distributed systems.

Distributed systems rely on **communication networks** to connect nodes and enable resource sharing. Important aspects:

#### 1. Network Types

- **Local Area Networks (LANs)**:
  - Small geographic area (building, campus).
  - High speed (e.g., Ethernet: 1 Gbps, 10 Gbps).
  - Used for clusters, data centers.

- **Wide Area Networks (WANs)**:
  - Connects distant sites (cities, countries).
  - Lower bandwidth, higher latency.
  - The Internet is the largest WAN.

- **Metropolitan Area Networks (MANs)**:
  - Cover a city or large campus.
  - Intermediate between LAN and WAN.

---

#### 2. Network Topologies

- **Bus Topology**:
  - All nodes share a common communication medium.
- **Star Topology**:
  - All nodes connected to a central hub/switch.
- **Ring Topology**:
  - Each node connected to two neighbors, forming a ring.
- **Mesh Topology**:
  - Nodes interconnect in a mesh; may be partial or full.

Modern systems usually use **switched Ethernet** with **star/mesh-like** physical topology.

---

#### 3. Switching Techniques

- **Circuit Switching**:
  - Dedicated path reserved for entire session.
  - Used in traditional telephone networks.
  - Not common in modern distributed systems.

- **Packet Switching**:
  - Data split into packets and routed independently.
  - Used in IP networks (Internet).
  - More efficient and flexible.

---

#### 4. Protocol Stack (TCP/IP Model)

- **Application Layer**:
  - Protocols: HTTP, FTP, SMTP, RPC, etc.
  - Provides application-level services.

- **Transport Layer**:
  - **TCP** (reliable, connection-oriented).
  - **UDP** (unreliable, connectionless, low overhead).

- **Network Layer**:
  - **IP** (Internet Protocol) for addressing and routing.

- **Link/Physical Layer**:
  - Ethernet, Wi-Fi, etc.

Distributed systems often build **higher-level communication abstractions** (e.g., RPC, message queues) on top of TCP/IP.

---

#### 5. Communication Patterns

- **Unicast**: One-to-one communication.
- **Broadcast**: One-to-all (within a network).
- **Multicast**: One-to-many (selected group).
- **Anycast**: One-to-any (one of several possible nodes).

Certain distributed algorithms (e.g., group communication, replication) rely on **multicast** and **broadcast**.

---

#### 6. Quality of Service (QoS)

- Requirements:
  - **Bandwidth**, **latency**, **jitter**, **reliability**.
- Some distributed applications (e.g., multimedia, real-time) require guarantees about QoS.

---

**Conclusion**:  
Communication networks in distributed systems range from **LANs to WANs**, using mainly **packet-switched** technologies and **TCP/IP** protocols. The network characteristics (topology, speed, reliability) strongly affect the **design and performance** of distributed algorithms and systems.

---

### 2(b) Discuss the theoretical foundations of distributed systems.

The **theoretical foundations** provide formal models and concepts to reason about behavior, correctness, and limitations of distributed systems.

#### 1. Models of Distributed Systems

- **Synchronous Model**:
  - Known bounds on message delay and process execution times.
  - Easier to reason about; not realistic in many wide-area systems.

- **Asynchronous Model**:
  - No bounds on message delays or process speeds.
  - Closer to reality (e.g., Internet).
  - Many impossibility results (e.g., FLP result) assume this model.

- **Partially Synchronous Model**:
  - System is mostly asynchronous but with some unknown bounds that eventually hold.

---

#### 2. Communication and Clocks

- **Logical Clocks (Lamport Clocks)**:
  - Provide a way to order events causally without a global physical clock.
- **Vector Clocks**:
  - Capture causality more precisely than Lamport clocks.
- These clocks formalize **“happened-before”** relation and are used in **causal ordering**, **debugging**, and **consistency protocols**.

---

#### 3. Global States and Snapshots

- A **global state** is a collection of local states of all processes and channels.
- **Chandy–Lamport snapshot algorithm**:
  - Captures a **consistent global state** without stopping the system.
- Used in **checkpointing**, **deadlock detection**, and **stable property detection**.

---

#### 4. Consensus and Agreement Problems

- **Consensus problem**:
  - Multiple processes must agree on a single value (e.g., commit/abort).
- Important for:
  - **Distributed transactions**, **leader election**, **replication**, **state machine replication**.
- The **FLP impossibility result**:
  - In a purely asynchronous system with even one potential crash failure, **deterministic consensus** is impossible.
- Practical consensus algorithms (Paxos, Raft) operate under **additional assumptions** (timeouts, failure detectors, etc.).

---

#### 5. Mutual Exclusion and Synchronization Theory

- **Distributed mutual exclusion**:
  - Access to a shared resource must be controlled so that only one process at a time can use it.
- Metrics:
  - **Message complexity**, **synchronization delay**, **fairness**, **fault tolerance**.
- Various algorithms (Lamport, Ricart–Agrawala, token-based, quorum-based) are analyzed based on these criteria.

---

#### 6. Formal Models (Graphs, Automata, Process Calculi)

- Systems are modeled as:
  - **Graphs** (nodes as processes, edges as communication channels).
  - **State transition systems / automata**.
  - **Process algebras** (e.g., CSP, π-calculus).
- These models allow **formal verification** of properties:
  - **Safety** (nothing bad happens).
  - **Liveness** (something good eventually happens).

---

**Conclusion**:  
The theoretical foundations include **models of time and communication**, **logical clocks**, **global states**, **consensus theory**, and **formal modeling techniques**. They help in proving **correctness, performance bounds, and impossibility results** in distributed systems.

---

### 3(a) Explain Lamport’s Logical Clocks.

In a distributed system, there is no global physical clock. **Lamport’s Logical Clocks** provide a way to **order events** based on the **causal relationship** between them.

#### 1. Happened-Before Relation (→)

- Defined by Leslie Lamport:
  - If events **a** and **b** are in the **same process**, and **a** occurs before **b**, then **a → b**.
  - If **a** is the sending of a message and **b** is the receipt of the same message, then **a → b**.
  - If **a → b** and **b → c**, then **a → c** (transitivity).
- If neither **a → b** nor **b → a**, then **a** and **b** are **concurrent**.

---

#### 2. Logical Clock Rules

Each process **Pi** maintains an integer **clock Ci**:

- **Rule 1 (Increment)**:
  - Before each event at process **Pi**, set:  
    Ci := Ci + 1

- **Rule 2 (Send)**:
  - When process **Pi** sends a message **m**, it includes **timestamp T = Ci** with the message.

- **Rule 3 (Receive)**:
  - When process **Pj** receives a message **m** with timestamp **T**, it sets:  
    Cj := max(Cj, T) + 1

These rules ensure that **if a → b, then C(a) < C(b)**.

---

#### 3. Properties and Uses

- **Causal ordering**:
  - If event **a** causally precedes **b**, then **C(a) < C(b)**.
- **Total ordering**:
  - If needed, we can break ties by using **(C(e), process_id)** as a pair.
- **Used in**:
  - Distributed mutual exclusion.
  - Ordering of events in logs.
  - Debugging and detecting causality.

---

#### 4. Limitations

- If **C(a) < C(b)**, it does **not guarantee** that **a → b** (only the other direction holds).
- It cannot distinguish between **causal** and **concurrent** events with the same order of timestamps.

---

**Conclusion**:  
Lamport’s logical clocks assign **monotonically increasing timestamps** to events to respect the **happened-before relation**. They are simple and useful for **causal ordering**, but do not capture full causality like **vector clocks**.

---

### 3(b) Describe Vector Clocks.

**Vector clocks** are an extension of logical clocks that capture **full causality** between events.

#### 1. Basic Idea

- Each process **Pi** maintains a **vector Vi** of length **N** (number of processes).
  - **Vi[j]** is process **Pi**’s knowledge of the **logical time at process Pj**.

---

#### 2. Rules for Vector Clocks

Let **Vi** be the vector clock at process **Pi**.

- **Rule 1 (Local Event at Pi)**:
  - Before executing an event:  
    Vi[i] := Vi[i] + 1

- **Rule 2 (Send Message from Pi)**:
  - Before sending, update as in Rule 1.
  - Attach **Vi** as the **timestamp vector** of the message.

- **Rule 3 (Receive Message at Pj)**:
  - On receiving message with vector timestamp **Vmsg**:
    - For each k:  
      Vj[k] := max(Vj[k], Vmsg[k])
    - Then increment its own component:  
      Vj[j] := Vj[j] + 1

---

#### 3. Comparing Two Vector Timestamps

For two events with vector timestamps **V(a)** and **V(b)**:

- **a → b** (a causally precedes b) if:
  - For all k: V(a)[k] ≤ V(b)[k]  
  - And for at least one k: V(a)[k] < V(b)[k]

- **a and b are concurrent** if:
  - Neither V(a) ≤ V(b) nor V(b) ≤ V(a) in the above sense.

Thus, vector clocks can **detect concurrency**.

---

#### 4. Applications

- **Detecting causal dependencies** in:
  - Distributed debugging.
  - Versioning in distributed databases.
  - Causal multicast and consistent snapshots.

---

#### 5. Limitations

- Vector size is **O(N)** (where N is number of processes).
- For very large or dynamic systems (N large or changing), vector clocks become costly.

---

**Conclusion**:  
Vector clocks provide a mechanism to **fully capture causality** among events in a distributed system. Unlike Lamport clocks, they can **distinguish concurrent events**, at the cost of maintaining a vector of size equal to the number of processes.

---

### 4(a) Explain the concept of Global State in a distributed system.

A **global state** is a **snapshot** of the entire distributed system at some logical time.

#### 1. Components of a Global State

- The global state consists of:
  - **Local state** of each process (contents of variables, program counter, etc.).
  - **State of communication channels** (messages in transit but not yet received).

Formally:

Global State = { local state of P1, local state of P2, ..., channel states }

---

#### 2. Challenges

- There is **no global clock**, and processes do not have a shared notion of time.
- Each process runs at its own speed, messages are delayed arbitrarily.
- Taking a consistent snapshot is non-trivial.

---

#### 3. Consistent Global State

- A global state is **consistent** if it could have occurred during **some valid execution** of the system.
- In terms of cuts:
  - A consistent global state does **not violate causality**:
    - If an event **b** is in the global state and **a → b**, then **a** must also be in the global state.

---

#### 4. Chandy–Lamport Snapshot Algorithm (Informal)

- **Goal**: Record a **consistent global state** without stopping the system.
- **Idea**:
  - Processes exchange **marker messages** to indicate points where they record their local state.
  - Messages in transit on channels are recorded based on markers.
- Resulting snapshot corresponds to a **consistent cut**.

---

#### 5. Uses of Global State

- **Checkpointing and Recovery**:
  - Save consistent global states periodically; use them to recover after failures.
- **Deadlock Detection**:
  - Examine global state to see if there is a set of processes waiting on each other.
- **Detection of stable properties**:
  - Properties that, once true, remain true (e.g., “termination”, “deadlock”) can be detected using global states.

---

**Conclusion**:  
The global state of a distributed system captures **all local states and channel states** at a logical instant. Because of lack of global time, algorithms like **Chandy–Lamport** are used to construct **consistent global states** for many purposes including **recovery and deadlock detection**.

---

### 4(b) What is a cut of a distributed computation?

A **cut** is a conceptual tool used in analyzing distributed computations.

#### 1. Definition

- A distributed computation is represented as:
  - A set of **events** across processes.
  - Connected by the **happened-before** relation.
- A **cut** is a subset of all events such that, for each process, either:
  - The cut contains some initial segment of that process’s events, or
  - It contains none of them.

Graphically, a cut is like drawing a curved line across the space–time diagram of the system.

---

#### 2. Consistent vs Inconsistent Cut

- A **consistent cut**:
  - If an event **b** is in the cut and **a → b**, then **a is also in the cut**.
  - Does not “see” an effect without its cause.
- An **inconsistent cut**:
  - Contains an event **b** but **misses some causal predecessor a** (a → b, but a is not in the cut).
  - Violates causality.

---

#### 3. Relationship to Global State

- Each cut corresponds to a **global state**:
  - The local state of each process at the last event included in the cut for that process.
  - Channel states determined by which messages have been sent but not yet received at the cut.
- **Consistent cuts** correspond to **consistent global states**.

---

**Conclusion**:  
A **cut** is a set of events representing a possible “snapshot line” through a distributed computation. **Consistent cuts** preserve causality and correspond to valid **global states** of the system.

---

### 5(a) Explain the problem of termination detection in distributed systems.

**Termination detection** is the problem of determining when a **distributed computation has finished**, i.e., when no process is active and no messages are in transit.

#### 1. Why It Is Difficult

- There is **no central observer** with complete knowledge.
- **Message delays** and asynchronous execution:
  - A process may be idle but might later receive a message and become active again.
- We must ensure:
  - No process is active.
  - No messages are **traveling in the network** (in transit).

---

#### 2. Formal Conditions

Distributed computation is **terminated** when:

1. **Every process is passive/idle** (no more computation to perform).
2. **No messages in transit** (no message that was sent but not yet received).

Both conditions must hold simultaneously.

---

#### 3. Approaches to Termination Detection

- **Centralized algorithms**:
  - A special **coordinator** collects information (active/passive state, message counts) to decide termination.
- **Distributed algorithms**:
  - Use **token circulation** (e.g., Dijkstra–Scholten, Safra’s algorithm).
  - The token carries information about ongoing activity.

---

#### 4. Example: Token-Based Idea (Conceptual)

- A token circulates logically over processes in a ring.
- Each process:
  - Updates token with info about whether it has sent or received messages.
- When the token returns to the initiator with indication that there is **no outstanding work**, termination is declared.

---

#### 5. Uses

- Termination detection is important for:
  - **Garbage collection**.
  - **Distributed search algorithms**.
  - Any algorithm where work is generated dynamically and distributed.

---

**Conclusion**:  
Termination detection in distributed systems is challenging due to **asynchrony and lack of global knowledge**. Algorithms must reliably detect the moment when all processes are passive and no messages are in transit, often using specialized **token or control messages**.

---

### 5(b) Explain process synchronization and deadlock handling in distributed operating systems.

#### 1. Process Synchronization

In a distributed system, processes run on different nodes but must often **coordinate access to shared resources**.

- **Goals**:
  - Ensure **mutual exclusion** for critical sections.
  - Maintain **ordering constraints** (e.g., producer–consumer).
  - Avoid inconsistent data.

- **Methods**:
  - **Distributed mutual exclusion algorithms**:
    - **Non-token-based** (e.g., Lamport’s, Ricart–Agrawala).
    - **Token-based** (e.g., token ring, Suzuki–Kasami).
  - **Clock-based synchronization**:
    - Use logical or vector clocks to order events.
  - **Barrier synchronization**:
    - All processes must reach a certain point before any proceed.

---

#### 2. Deadlocks in Distributed Systems

- **Deadlock**: A set of processes is **blocked forever**, each waiting for resources held by others in the set.
- Conditions (same as centralized systems):
  1. Mutual exclusion.
  2. Hold and wait.
  3. No preemption.
  4. Circular wait.

In a distributed system, deadlock detection/handling is harder because:

- Information is **distributed** among nodes.
- Communication is **asynchronous**.

---

#### 3. Deadlock Handling Approaches

1. **Deadlock Prevention**:
   - Design the system so that at least one of the necessary conditions is never satisfied.
   - Example: Impose a **global ordering** on resource acquisition.

2. **Deadlock Avoidance**:
   - Requires advance information about resource requirements (like **Banker’s algorithm**).
   - Hard to implement in distributed systems due to lack of global state.

3. **Deadlock Detection and Recovery**:
   - More common in distributed systems.
   - System periodically checks for deadlocks and then recovers.

---

#### 4. Distributed Deadlock Detection

- **Distributed Wait-For Graph (WFG)**:
  - Each node maintains a local WFG of processes and resources.
  - Algorithms attempt to construct a **global WFG** or detect cycles using messages.
- **Techniques**:
  - **Path-pushing**: Information about waits is propagated to detect cycles.
  - **Probe-based algorithms**: Special probe messages circulate to detect circular waits.

---

#### 5. Recovery from Deadlock

- Once a deadlock is detected:
  - **Abort** one or more processes (victims).
  - **Preempt resources** if possible.
- Criteria for victim selection:
  - Priority, amount of work done, number of resources held, etc.

---

**Conclusion**:  
Process synchronization in distributed OS focuses on **coordinating processes** using distributed mutual exclusion and clock-based ordering. **Deadlock handling** involves preventing, avoiding, or more commonly **detecting and recovering from deadlocks** using distributed algorithms over wait-for graphs.

---

## UNIT–II

---

### 1(a) Explain the classification of distributed mutual exclusion algorithm.

Distributed mutual exclusion (DME) algorithms ensure that **only one process at a time** enters the **critical section** that accesses shared resources, without using shared memory.

They are generally classified as:

#### 1. Token-Based Algorithms

- **Idea**:
  - A unique **token** circulates among processes.
  - Possession of the token gives **permission** to enter the critical section.
- **Examples**:
  - Token ring algorithm.
  - Suzuki–Kasami’s broadcast algorithm.
  - Raymond’s tree-based algorithm.
- **Characteristics**:
  - No need for request/reply messages when token is present.
  - Mutual exclusion is simple: at most one token.
- **Drawbacks**:
  - Token **loss** is problematic.
  - Token **recovery** and **fault tolerance** are non-trivial.

---

#### 2. Non-Token-Based (Permission-Based) Algorithms

- **Idea**:
  - No special token.
  - When a process wants to enter critical section, it sends **request messages** to other processes and waits for their **permissions (replies)**.
- **Examples**:
  - Lamport’s algorithm.
  - Ricart–Agrawala algorithm.
  - Maekawa’s quorum-based algorithm (hybrid).
- **Characteristics**:
  - Use **timestamps** (logical clocks) to order requests.
  - Every process maintains a **request queue** or state information.
- **Drawbacks**:
  - Incur higher **message complexity**.
  - Need to handle **failures** of coordinator or processes.

---

#### 3. Centralized vs Distributed Control

- **Centralized algorithms**:
  - A **single coordinator** manages the critical section.
  - Simple but suffers from **single point of failure** and **bottleneck**.
- **Fully distributed algorithms**:
  - All processes are symmetric; no single coordinator.
  - More robust, but more complex.

---

#### 4. Quorum-Based Algorithms

- **Idea**:
  - Instead of contacting **all processes**, a process contacts a **subset (quorum)**.
  - Quorums are arranged so that **any two quorums intersect**.
- **Example**:
  - Maekawa’s algorithm.
- **Advantages**:
  - Reduces number of messages compared to all-to-all.
- **Issues**:
  - Possible deadlocks and starvation if not carefully designed.

---

**Conclusion**:  
Distributed mutual exclusion algorithms are classified mainly into **token-based** and **non-token-based (permission-based)**, as well as **centralized** vs **distributed** and **quorum-based** approaches. Each class has different trade-offs in terms of **message complexity, fault tolerance, and fairness**.

---

### 1(b) Describe how distributed mutual exclusion algorithms are categorized.

Distributed mutual exclusion algorithms can be categorized along several dimensions:

#### 1. Based on Control Mechanism

- **Token-based**:
  - Use a **single circulating token**.
- **Non-token-based (permission-based)**:
  - Use **request-reply messages**; no special token.

---

#### 2. Based on Centralization

- **Centralized algorithms**:
  - Single **coordinator** grants and releases permissions.
  - Simpler logic but centralized bottleneck.
- **Decentralized algorithms**:
  - Multiple coordinators; each responsible for a subset of resources.
- **Fully distributed algorithms**:
  - All processes are equal; decisions are made collectively.

---

#### 3. Based on Communication Pattern

- **All-to-all**:
  - Requester sends to **all** processes and waits for all replies (e.g., Lamport, Ricart–Agrawala).
- **Quorum-based**:
  - Requester communicates with only a **subset of processes** (quorum).
- **Hierarchical or tree-based**:
  - Requests travel along a **tree structure** (Raymond’s algorithm).

---

#### 4. Based on Performance Metrics

- **Message complexity**:
  - Number of messages per critical section entry (e.g., O(N), O(log N)).
- **Synchronization delay**:
  - Waiting time between one process leaving and another entering critical section.
- **Throughput and scalability**:
  - How performance changes with growing N.

---

#### 5. Based on Fault Tolerance and Fairness

- **Fault-tolerant vs non-fault-tolerant**:
  - Ability to handle failures of processes or communication links.
- **Fair vs unfair**:
  - Whether **starvation** is possible; whether requests are served in **FIFO** or **timestamp** order.

---

**Conclusion**:  
DME algorithms are categorized based on **mechanism (token/non-token)**, **degree of centralization**, **communication pattern**, **performance metrics**, and **fault-tolerance/fairness** properties. This classification helps in choosing a suitable algorithm for a specific distributed application.

---

### 2(a) Describe Lamport’s Algorithm for distributed mutual exclusion.

Lamport’s algorithm is a **non-token-based, fully distributed** mutual exclusion algorithm using **logical clocks**.

#### 1. Basic Idea

- Every process maintains a **logical clock** and a **request queue**.
- Mutual exclusion is achieved by:
  - Timestamping **requests**.
  - Ordering them by **(timestamp, process ID)**.
  - Ensuring all processes agree on this order.

---

#### 2. Data Structures

At each process **Pi**:

- **Ci** – Lamport’s logical clock.
- **Request queue** – ordered by (timestamp, process ID).
- Messages:
  - REQUEST (TS, i)
  - REPLY (i)
  - RELEASE (i)

---

#### 3. Algorithm Steps

**(i) Requesting the Critical Section**

1. Pi increments its clock: Ci := Ci + 1.
2. Sends REQUEST (Ci, i) to **all other processes, including itself**.
3. Inserts the request into its **local request queue**.
4. Waits until:
   - Its own request is **at the head of the queue**, and
   - It has received **REPLY** from **all other processes**.

**(ii) Receiving a REQUEST (T, j) at Pi**

1. Update clock: Ci := max(Ci, T) + 1.
2. Insert (T, j) into Pi’s **request queue**.
3. Send REPLY (i) back to Pj.

**(iii) Releasing the Critical Section**

1. Pi removes its own request from its **request queue**.
2. Sends a RELEASE (i) message to all other processes.

**(iv) Receiving a RELEASE (j) at Pi**

1. Remove Pj’s request from **Pi’s request queue**.

---

#### 4. Why It Works

- **Total ordering of requests**:
  - Based on **(timestamp, process ID)**.
- Every process’s queue is ordered according to this total order.
- A process can enter the critical section **only when its request is at the head** and it knows that **all earlier requests are acknowledged**.

---

#### 5. Performance

- **Message complexity** per critical section entry:
  - REQUEST to (N−1) processes + REPLY from (N−1) + RELEASE to (N−1)  
    ≈ **3(N − 1)** messages.
- Provides **mutual exclusion**, **no deadlock**, and **no starvation** (requests are served in order).

---

**Conclusion**:  
Lamport’s algorithm uses **logical clocks and total ordering** of requests to achieve distributed mutual exclusion in a **fully distributed, non-token-based** way, at the cost of O(N) messages per critical section.

---

### 2(b) What are the key features of the Ricart–Agrawala Algorithm?

The **Ricart–Agrawala** algorithm is a **non-token-based**, fully distributed mutual exclusion algorithm that **reduces the message count** compared to Lamport’s algorithm.

#### Key Features:

1. **Two-Message Mutual Exclusion**
   - For each critical section entry, only:
     - **(N−1) REQUEST messages**
     - **(N−1) REPLY messages**
   - No separate RELEASE messages are required.

2. **Timestamped Requests**
   - Similar to Lamport’s algorithm, uses **logical timestamps**.
   - Requests are ordered by **(timestamp, process ID)**.

3. **Permission-Based Entry**
   - A process may enter the critical section only after receiving **REPLY** from **all other processes**.

4. **Deferred Replies**
   - When a process receives a REQUEST while it also wants the critical section:
     - It compares timestamps.
     - If its own request has **higher priority**, it **replies immediately**.
     - If its own request has **lower priority**, it **defers** reply until it exits the critical section.

5. **No Central Coordinator and No Token**
   - Fully **distributed**, all processes are symmetric.
   - No special coordinator or token to manage.

6. **Correctness Properties**
   - **Mutual exclusion**: Only one process can hold the critical section.
   - **Freedom from deadlock**: Circular wait is avoided by timestamp ordering.
   - **No starvation**: Requests with earlier timestamps are eventually granted.

7. **Message Complexity**
   - **2(N−1)** messages per critical section entry.
   - More efficient than Lamport’s 3(N−1) messages.

---

**Conclusion**:  
Ricart–Agrawala is a **timestamp-based, permission-based** mutual exclusion algorithm characterized by **2(N−1) messages per entry**, **deferred replies**, **no central coordinator**, and **no token**, while ensuring mutual exclusion, no deadlock, and no starvation.

---

### 3(a) Explain the concept of quorums in Maekawa’s Algorithm.

Maekawa’s algorithm is a **quorum-based** distributed mutual exclusion algorithm.

#### 1. Quorum Concept

- A **quorum** is a **subset** of processes such that:
  - Each process Pi is associated with a **quorum set Qi**.
  - For any two processes Pi and Pj, **Qi ∩ Qj ≠ ∅** (they share at least one common member).

This intersection property ensures that **no two processes can enter the critical section simultaneously**, because they have at least one **common process** that can grant permission to only one at a time.

---

#### 2. Structure of Quorums

- Quorums are designed so that:
  - Each **Qi** is relatively small (e.g., O(√N) for N processes).
  - Every pair of quorums **intersects**.

---

#### 3. How Quorums Are Used

- When Pi wants to enter the critical section:
  - It sends **REQUEST** messages **only to processes in Qi** (its quorum).
  - It needs **permission from all members of Qi**.
- Since Qi and Qj intersect, two processes **cannot both get all permissions** simultaneously.

---

#### 4. Advantages of Using Quorums

- **Reduced message complexity**:
  - Instead of contacting **all N processes**, each process contacts only **|Qi|** ≈ O(√N).
- **Scalability**:
  - More scalable than all-to-all algorithms for large N.

---

#### 5. Issues and Limitations

- **Deadlock possibility**:
  - Under some conditions, circular waiting for permissions across quorums can arise.
- **Starvation**:
  - Without careful tie-breaking, some processes may be delayed indefinitely.
- Additional mechanisms (e.g., priority, ordering) are often needed.

---

**Conclusion**:  
In Maekawa’s algorithm, **quorums** are specially constructed subsets of processes with the **intersection property**, enabling mutual exclusion by obtaining permissions from a **small subset** rather than all processes, thus improving scalability.

---

### 3(b) Explain the main idea behind Suzuki–Kasami’s Broadcast Algorithm.

The **Suzuki–Kasami** algorithm is a **token-based** distributed mutual exclusion algorithm that uses **broadcast** messages.

#### 1. Main Ideas

1. **Single Token**:
   - There is one unique **token** in the system.
   - Only the process holding the token can enter the critical section.

2. **Broadcast Requests**:
   - A process that wants the token broadcasts a **REQUEST** message to all processes.
   - Each process maintains **request numbers** to track how many times each process has requested the token.

3. **Token Structure**:
   - Contains:
     - **Last request number served** for each process.
     - A **queue** of processes waiting for the token.

4. **Granting the Token**:
   - When a process with the token receives a REQUEST, it:
     - Updates its information.
     - If it is not in the critical section and the requesting process’s request is outstanding, it **sends the token** to that process, possibly after finishing its own use.

---

#### 2. Algorithm Behavior (High Level)

- When Pi wants to enter CS:
  - It increments its **request number** and broadcasts REQUEST(i, req_i) to all.
- Each Pj:
  - On receiving a request from Pi, stores the **largest request number** seen from Pi.
- The token holder:
  - On leaving CS, checks for **pending requests** (based on request numbers and last served).
  - Adds such processes to the token’s queue and passes the token accordingly.

---

#### 3. Features

- **Low message overhead when token is available**:
  - If a process already has the token, no messages needed to enter CS.
- **Message complexity**:
  - Each request requires **O(N)** messages (broadcast), but **no REPLY messages**.
- **Fairness**:
  - Requests are served in roughly **FIFO order**, according to request numbers.
- **No centralized coordinator**.

---

**Conclusion**:  
The Suzuki–Kasami algorithm uses a **single circulating token** and **broadcast requests** with request numbers to achieve mutual exclusion. Its key idea is to minimize messages when token is available and manage waiting processes via a **queue in the token**.

---

### 4(a) Summarize Singhal's Heuristic Algorithm.

Singhal’s algorithm is a **distributed mutual exclusion** algorithm that aims to reduce message overhead using **heuristics**.

#### 1. Key Ideas

1. **Dynamic Request Sets**:
   - Unlike algorithms that send requests to all processes, Singhal’s algorithm uses **dynamic sets of processes** to contact.
   - Each process maintains a set of processes from which it needs permission.

2. **Heuristic Reduction of Messages**:
   - Heuristics are used to **shrink the request set** over time based on observed communication behavior.
   - Processes adapt to patterns, contacting **only those likely to cause conflicts**.

3. **Priority and Timestamps**:
   - As in other non-token-based algorithms, **timestamps** are used to order requests.
   - Processes may defer replies based on priority.

---

#### 2. Basic Operation (High Level)

- When a process wants to enter CS:
  - It sends requests **only to processes in its current request set**.
- When it exits CS:
  - It may **adjust its request set** based on which processes requested the CS concurrently.
- Over time:
  - The request sets converge to smaller subsets, optimized for typical conflict patterns.

---

#### 3. Advantages

- **Reduced message complexity**:
  - For many workloads, fewer messages than all-to-all algorithms like Lamport or Ricart–Agrawala.
- **Adaptive**:
  - Automatically adapts to the normal **communication pattern** of the system.

---

#### 4. Disadvantages

- **Complexity**:
  - More complex to implement and analyze.
- **Correctness**:
  - Must be carefully designed so that mutual exclusion, fairness, and absence of deadlock are preserved despite dynamic request sets.

---

**Conclusion**:  
Singhal’s heuristic algorithm dynamically adjusts the set of processes contacted for mutual exclusion, aiming to **reduce communication overhead** while still ensuring correctness, particularly in systems with predictable conflict patterns.

---

### 4(b) Explain the structure of Raymond’s Tree-Based Mutual Exclusion Algorithm.

Raymond’s algorithm is a **token-based**, **tree-structured** distributed mutual exclusion algorithm.

#### 1. Logical Tree Structure

- Processes are arranged in a **logical tree** (often a spanning tree).
- Each process has:
  - A **parent pointer** (towards the current direction of the token).
  - A **queue** of requests.

Conceptual tree (token initially at root):

```
       P1 (root, token)
      /    \
    P2      P3
   /  \    /  \
 P4  P5  P6  P7
```

---

#### 2. Main Data Structures

At each process **Pi**:

- **Holder**:
  - The process that Pi believes **currently holds the token** (could be itself).
- **Request queue**:
  - Queue of processes that have requested the token from Pi.

---

#### 3. Algorithm Behavior

1. **Requesting the Token**

   - If Pi wants to enter CS and **does not have the token**:
     - It **enqueues itself** in its local request queue.
     - If this is the **only request** and Holder ≠ Pi:
       - It sends a **REQUEST** message to **Holder**.
   - Requests propagate **up the tree** towards the current token holder.

2. **Receiving a REQUEST at Pk**

   - Pk adds the requester ID to its queue.
   - If Pk is **not currently requesting** the token (and doesn’t have the token):
     - It forwards a REQUEST towards its **Holder** (up the tree).

3. **Receiving the Token**

   - When a process receives the token:
     - It sets **Holder := self**.
     - If its **local request queue** is non-empty:
       - It **dequeues** the first process Q.
       - If Q = self:
         - It enters the **critical section**.
       - Else:
         - It passes the token to Q (update Holder, send token).
         - Removes Q from queue.

4. **Releasing CS**

   - After leaving CS, if its request queue is non-empty:
     - It passes the token to the **next process** in its queue.

---

#### 4. Properties

- **Mutual Exclusion**:
  - Only one token; only token holder can enter CS.
- **Message Complexity**:
  - Request and token messages travel along the **unique path in the tree** between requester and holder.
  - Average complexity is **O(log N)** for balanced tree.
- **Fairness**:
  - Requests are served roughly in **FIFO order** along paths.

---

**Conclusion**:  
Raymond’s tree-based algorithm organizes processes into a **logical tree**, with requests and the token sent along parent–child links. It offers efficient mutual exclusion with **logarithmic message complexity** in balanced trees.

---

### 5(a) Differentiate between token-based and non-token-based mutual exclusion algorithms.

| Aspect                    | Token-Based Algorithms                           | Non-Token-Based Algorithms                          |
|---------------------------|--------------------------------------------------|-----------------------------------------------------|
| Basic Mechanism           | Use a **single circulating token**; holder can enter CS | Use **request-reply** messages, no special token    |
| Example Algorithms        | Token ring, Suzuki–Kasami, Raymond’s algorithm  | Lamport, Ricart–Agrawala, Maekawa (hybrid)         |
| Entry Condition           | Process must **possess the token**              | Process must receive **permission from others**     |
| Message Complexity        | Often **O(1)** or O(log N) per entry if token nearby; sometimes O(N) | Typically **O(N)** or more (REQUEST + REPLY)       |
| Failure Handling          | Token **loss** is critical; token recovery needed | Process failures affect replies; may need timeouts |
| Bottlenecks               | Token holder is only one in CS, token path matters | Potential bottleneck in **coordinator** or many replies |
| Fairness                  | Usually fair via queue in token or ring order   | Fairness achieved by timestamp ordering and queues  |
| Simplicity                | Conceptually simple (one token)                 | Logic more complex; requires ordering requests      |

---

**Conclusion**:  
Token-based algorithms rely on **a unique token** for granting access to critical sections, whereas non-token-based algorithms rely on **explicit permissions** via messages. Each has advantages and drawbacks in terms of **message complexity, fault tolerance, and implementation complexity**.

---

### 5(b) Why is deadlock possible in Maekawa’s Algorithm?

In Maekawa’s quorum-based algorithm, **deadlock is possible** due to the way **quorums and permissions** interact.

#### 1. Quorum Intersections and Local Permissions

- Each process Pi:
  - Needs permission from all members of its quorum **Qi**.
- Since quorums intersect, processes can **block each other** indirectly.

---

#### 2. Circular Wait Scenario

- Suppose processes P1, P2, P3 each have overlapping quorums.
- Consider a situation:
  - P1 holds permission from some nodes in Q1, and waits for others.
  - P2 holds permission from some nodes in Q2, and waits for others.
  - P3 holds permission from some nodes in Q3, and waits for others.
- Due to overlapping quorums, a cycle can form:
  - Each process holds some permission needed by another process, leading to **circular wait**, a necessary condition for deadlock.

---

#### 3. Lack of Global Ordering

- Maekawa’s basic algorithm:
  - Does not impose a strict **global ordering on requests** like Lamport’s timestamps.
  - Local request queues at each node may create **inconsistent global ordering**, enabling circular waits.

---

#### 4. No Preemption of Granted Permissions

- Once a node grants permission to a process, it typically does not **revoke** it until:
  - The process releases it after using the critical section.
- If multiple processes hold partial permissions from different quorums and no one can complete, the system enters **deadlock**.

---

#### 5. Remedies (High Level)

- To avoid deadlock, extended versions of Maekawa’s algorithm introduce:
  - **Priority schemes** (e.g., timestamps).
  - **Preemption** of permissions.
  - Specific **deadlock detection and resolution** strategies.

---

**Conclusion**:  
Deadlock is possible in Maekawa’s algorithm because overlapping **quorums** and independent local decisions can create **circular waits** for permissions, with no inherent global ordering or preemption to break these cycles.


