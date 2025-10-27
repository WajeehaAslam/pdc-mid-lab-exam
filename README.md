Parallel and Distributed Computing – Image Processing
Project Overview

This project demonstrates three approaches to image preprocessing (resize to 128x128 and watermarking) using:

Sequential Processing

Parallel Processing (Multiprocessing / ThreadPoolExecutor)

Simulated Distributed Processing (using multiprocessing.Manager)

The dataset includes four folders: Cars, Flowers, Cat, and Dogs.

Performance Comparison Table
Method Total Time (seconds) Workers/Nodes Used Speedup
Sequential 0.55 1 worker 1.00x
Parallel (2) 1.16 2 workers 0.79x
Parallel (4) 0.97 4 workers 0.94x
Parallel (8) 1.63 8 workers 0.56x
Distributed (2 nodes) 1.20 2 nodes 15.19x
Best Number of Workers

The best performance was observed with 4 workers in the parallel configuration.
Although 8 workers introduced more overhead and context switching, 4 workers provided a better balance between CPU utilization and process management, leading to stable performance.

Discussion

Parallelism improved performance by allowing multiple images to be processed simultaneously across CPU cores, reducing the overall execution time compared to the sequential approach.
However, the speedup was not linear due to several bottlenecks:

I/O operations (reading and writing image files) are still sequential and dominate total time.

The dataset is relatively small, so parallel overhead reduces the gains.

Excessive worker processes increase context switching and memory usage.
Future improvements could include using asynchronous I/O operations, batching, or GPU acceleration (e.g., CUDA) for faster image transformations.

Folder Structure
📂 parallel and distributing comp
│── cars-20251027T101016Z-1-001/
│── Cat-20251027T101016Z-1-001/
│── dogs-20251027T101019Z-1-001/
│── Flowers-20251027T101023Z-1-001/
│── output_seq/
│── output_parallel/
│── output_distributed/
│── sequential_process.py
│── parallel_process.py
│── distributed_simulation.py
│── report.txt
└── Readme.md

Author

Wajeeha Aslam
BS Computer Science – COMSATS University, Lahore
Course: Parallel and Distributed Computing
Date: October 27, 2025
