
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
