flowchart TD

    A[Start Notebook Execution] --> B[Import Libraries & Dependencies]

    B --> C[Create Sample Document Object]

    C --> D[Read All PDFs from Directory]

    D --> E{PDF Files Found?}
    E -->|Yes| F[Load PDFs Using PyPDFLoader]
    E -->|No| Z[End Process]

    F --> G[Attach Metadata to Each Page]
    G --> H[Aggregate All Documents]

    H --> I[Split Documents into Chunks]
    I --> J[Initialize Text Splitter]
    J --> K[Create Overlapping Text Chunks]

    K --> L[Initialize Embedding Manager]
    L --> M[Load Transformer Embedding Model]

    M --> N[Generate Embeddings for All Chunks]

    N --> O[Initialize Chroma Vector Store]
    O --> P[Persist Vector Store on Disk]

    P --> Q[Add Chunks + Embeddings to Vector Store]

    Q --> R[Initialize RAG Retriever]

    R --> S[User Provides Query]
    S --> T[Generate Query Embedding]

    T --> U[Perform Vector Similarity Search]
    U --> V{Similarity >= Threshold?}

    V -->|Yes| W[Collect Relevant Documents]
    V -->|No| X[Discard Result]

    W --> Y[Return Top-K Relevant Chunks]
    Y --> Z[End Retrieval]
