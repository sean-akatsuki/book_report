
## think model
```mermaid

flowchart TD
    %% Styling Definition
    classDef startFill fill:#1f2937,stroke:#374151,color:#fff,stroke-width:2px;
    classDef processFill fill:#1e3a8a,stroke:#3b82f6,color:#fff,stroke-width:1px;
    classDef decisionFill fill:#581c87,stroke:#a855f7,color:#fff,stroke-width:1px;
    classDef resultFill fill:#064e3b,stroke:#10b981,color:#fff,stroke-width:1px;

    Start(["Problem Statement & Input Data"]):::startFill --> Step1

    %% Step 1: Physical Characteristics
    subgraph Step1 ["Step 1: Analyze Physical Characteristics"]
        S1_Data{"Is Data Dynamic or Static?"}:::decisionFill
        S1_Data -- Static --> S1_Arr["Array / Contiguous Memory<br/>(Cache Friendly, O(1) Indexing)"]:::processFill
        S1_Data -- Dynamic --> S1_Ord{"Is Order Needed?"}:::decisionFill
        
        S1_Ord -- Natural/Pre-sorted --> S1_TP["Two Pointers / Binary Search"]:::processFill
        S1_Ord -- Dynamic Sorting --> S1_Tree["Balanced BST / Heap"]:::processFill
        S1_Ord -- Unordered --> S1_Hash["Hash Table / Linked List"]:::processFill
    end

    Step1 --> Step2

    %% Step 2: High-Frequency Operations
    subgraph Step2 ["Step 2: Identify Core Operations"]
        S2_Op{"What is the Primary Operation?"}:::decisionFill

        S2_Op -- "Exact Lookup (Key/Value)" --> Res_Hash["Hash Table (O(1))"]:::resultFill
        S2_Op -- "Dynamic Min/Max (Extremes)" --> Res_Heap["Heap / Priority Queue (O(1) Find, O(log N) Insert)"]:::resultFill
        S2_Op -- "FIFO (Sequential Tasks)" --> Res_Queue["Queue / BFS (O(1))"]:::resultFill
        S2_Op -- "LIFO / Undo / Nesting" --> Res_Stack["Stack / DFS / Monotonic Stack (O(1))"]:::resultFill
        S2_Op -- "Range Query & Updates" --> Res_Tree["Segment Tree / Fenwick Tree (O(log N))"]:::resultFill
        S2_Op -- "Prefix Matching" --> Res_Trie["Trie / Prefix Tree (O(L))"]:::resultFill
        S2_Op -- "Disjoint Sets / Connectivity" --> Res_UF["Union-Find (O(α(N)))"]:::resultFill
    end

    Step2 --> Step3

    %% Step 3: Trade-offs
    subgraph Step3 ["Step 3: Evaluate Time-Space Trade-offs"]
        S3_Check{"Check Constraints"}:::decisionFill
        S3_Check -- "Strict Time Limit" --> T_Space["Trade Space for Time<br/>(Use Hash Maps, Memoization, Tries)"]:::processFill
        S3_Check -- "Strict O(1) Memory Limit" --> T_Time["Trade Time for Space<br/>(Use Two Pointers, In-place Swaps, Bit Manipulation)"]:::processFill
        S3_Check -- "Multiple Repeated Queries" --> T_Pre["Preprocess First<br/>(Build Trees or Sort O(N log N) -> Query O(log N))"]:::processFill
    end

    Step3 --> Step4

    %% Step 4: Verification
    subgraph Step4 ["Step 4: Final Verification & Choice"]
        Res_Final(["Selected Data Structure & Optimal Algorithm"]):::startFill
    end

```


## complexity of data structure
| Category | Data Structure | Access / Query (Avg) | Search / Find (Avg) | Insert / Add (Avg) | Delete / Remove (Avg) | Access / Query (Worst) | Search / Find (Worst) | Insert / Add (Worst) | Delete / Remove (Worst) | Space Complexity (Worst) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Linear** | **Array** | $O(1)$ | $O(n)$ | $O(n)$ | $O(n)$ | $O(1)$ | $O(n)$ | $O(n)$ | $O(n)$ | $O(n)$ |
| **Linear** | **Sorted Array** | $O(1)$ | $O(\log n)$ | $O(n)$ | $O(n)$ | $O(1)$ | $O(\log n)$ | $O(n)$ | $O(n)$ | $O(n)$ |
| **Linear** | **Dynamic Array** | $O(1)$ | $O(n)$ | $O(1)$ *(Amortized)* | $O(n)$ | $O(1)$ | $O(n)$ | $O(n)$ *(Realloc)* | $O(n)$ | $O(n)$ |
| **Linear** | **Singly-Linked List** | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ | $O(n)$ |
| **Linear** | **Doubly-Linked List** | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ | $O(n)$ |
| **Linear** | **Stack** | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ | $O(n)$ |
| **Linear** | **Queue / Deque** | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ | $O(n)$ |
| **Linear** | **Skip List** | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | $O(n)$ | $O(n)$ | $O(n)$ | $O(n)$ | $O(n \log n)$ |
| **Hash-Based** | **Hash Table / Map** | — | $O(1)$ | $O(1)$ | $O(1)$ | — | $O(n)$ | $O(n)$ | $O(n)$ | $O(n)$ |
| **Hash-Based** | **Hash Set** | — | $O(1)$ | $O(1)$ | $O(1)$ | — | $O(n)$ | $O(n)$ | $O(n)$ | $O(n)$ |
| **Hash-Based** | **Bloom Filter** | — | $O(k)$ | $O(k)$ | N/A | — | $O(k)$ | $O(k)$ | N/A | $O(m)$ |
| **Tree-Based** | **Binary Search Tree** | — | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | — | $O(n)$ | $O(n)$ | $O(n)$ | $O(n)$ |
| **Tree-Based** | **AVL Tree** | — | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | — | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | $O(n)$ |
| **Tree-Based** | **Red-Black Tree** | — | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | — | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | $O(n)$ |
| **Tree-Based** | **B-Tree / B+ Tree** | — | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | — | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | $O(n)$ |
| **Tree-Based** | **Splay Tree** | — | $O(\log n)$ *(Amortized)* | $O(\log n)$ *(Amortized)* | $O(\log n)$ *(Amortized)* | — | $O(n)$ | $O(n)$ | $O(n)$ | $O(n)$ |
| **Tree-Based** | **Segment Tree** | $O(\log n)$ | — | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | — | $O(\log n)$ | $O(\log n)$ | $O(n)$ |
| **Tree-Based** | **Fenwick Tree (BIT)** | $O(\log n)$ | — | $O(\log n)$ | N/A | $O(\log n)$ | — | $O(\log n)$ | N/A | $O(n)$ |
| **Tree-Based** | **Trie (Prefix Tree)** | — | $O(L)$ | $O(L)$ | $O(L)$ | — | $O(L)$ | $O(L)$ | $O(L)$ | $O(N \cdot L)$ |
| **Heap** | **Binary Heap** | — | $O(1)$ *(Find Min/Max)* | $O(\log n)$ | $O(\log n)$ *(Delete Min/Max)* | — | $O(1)$ *(Find Min/Max)* | $O(\log n)$ | $O(\log n)$ *(Delete Min/Max)* | $O(n)$ |
| **Heap** | **Binomial Heap** | — | $O(1)$ *(Find Min/Max)* | $O(1)$ *(Amortized)* | $O(\log n)$ *(Delete Min/Max)* | — | $O(1)$ *(Find Min/Max)* | $O(\log n)$ | $O(\log n)$ *(Delete Min/Max)* | $O(n)$ |
| **Heap** | **Fibonacci Heap** | — | $O(1)$ *(Find Min/Max)* | $O(1)$ | $O(\log n)$ *(Amortized)* | — | $O(1)$ *(Find Min/Max)* | $O(1)$ | $O(\log n)$ *(Amortized)* | $O(n)$ |
| **Graph & Special** | **Adjacency Matrix** | $O(1)$ *(Edge lookup)* | $O(V^2)$ *(Traversal)* | $O(1)$ *(Add edge)* | $O(1)$ *(Remove edge)* | $O(1)$ *(Edge lookup)* | $O(V^2)$ *(Traversal)* | $O(1)$ *(Add edge)* | $O(1)$ *(Remove edge)* | $O(V^2)$ |
| **Graph & Special** | **Adjacency List** | $O(\text{deg}(V))$ | $O(V + E)$ *(Traversal)* | $O(1)$ *(Add edge)* | $O(\text{deg}(V))$ | $O(\text{deg}(V))$ | $O(V + E)$ *(Traversal)* | $O(1)$ *(Add edge)* | $O(\text{deg}(V))$ | $O(V + E)$ |
| **Graph & Special** | **Union-Find (DSU)** | — | $O(\alpha(N))$ *(Find)* | $O(\alpha(N))$ *(Union)* | N/A | — | $O(\alpha(N))$ *(Find)* | $O(\alpha(N))$ *(Union)* | N/A | $O(N)$ |
| **Graph & Special** | **Suffix Tree** | — | $O(M)$ *(Pattern match)* | $O(N)$ *(Build)* | N/A | — | $O(M)$ *(Pattern match)* | $O(N)$ *(Build)* | N/A | $O(N)$ |

Variable Glossary
- $n / N$: Number of elements / items in the data structure.
- $V$: Number of vertices in a graph.
- $E$: Number of edges in a graph.
- $L$: Length of a string key.
- $M$: Length of a search pattern string.
- $k$: Number of hash functions (Bloom Filter).
- $m$: Size of the bit array (Bloom Filter).
- $\alpha(N)$: Inverse Ackermann function (effectively $O(1)$ in practice).
