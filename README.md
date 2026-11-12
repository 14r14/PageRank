# PageRank Algorithm

> Author Note: This project relies on minimal AI assistance. Almost all architecture, data structures, algorithms, and implementations are written by hand from scratch.

A modular, high-performance search engine built in modern C++. The project is organized as a unified workspace composed of dedicated subsystems responsible for crawling, indexing, distributed task execution, and ranking.

### Project Status
- Completed an *Early Prototype* of the **Crawler**:
    - Non-parallelized, single-threaded crawler with DOM URL extraction and hash-based URL deduplication.
---
### Tech Stack & Dependencies
* Language: C++20
* Build System: CMake (>= 3.20)
* Compiler: Clang (clang++) or GCC with ARM64 / x86_64 target support
#### Core Libraries:
- **libcurl** - for network operations
- **lexbor** - for HTML parsing & DOM manipulation
- **xxHash** (XXH3 variant) - for ultra-fast, non-cryptographic hashing
- **RocksDB** - for LSM-Tree on-disk storage of found frontiers and Stage-2 URL deduplication
- moodycamel's ConcurrentQueue - for multi-producer, multi-consumer FIFO queue of frontiers
---
### Roadmap
- **Crawler Subsystem**: Transition from the current single-threaded prototype to a multithreaded/asynchronous event loop.
- **Web Graph & Topology**: Finalize the streaming edge-ingestion pipeline to map hashed URLs to contiguous 32-bit vertex IDs. Implement an efficient graph representation of the pages.
- **PageRank Engine**: Implement parallel power-iteration using OpenMP/SIMD vectorization for returning rankings.
- **Worker Pool & Distributed Infrastructure**: Design an IPC/RPC protocol to coordinate URL frontier partitioning across independent fetcher workers.
