# 🖼️ Parallel and Distributed Computing – Image Processing Project

## 📘 Overview
This project demonstrates three different approaches to image preprocessing (resizing images to **128x128** and adding a watermark) using:

- **Sequential Processing**
- **Parallel Processing** (via `multiprocessing` / `ThreadPoolExecutor`)
- **Simulated Distributed Processing** (using `multiprocessing.Manager`)

Each method processes images from four datasets: **Cars**, **Flowers**, **Cat**, and **Dogs**.

---

## 📂 Folder Structure

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

yaml
Copy code

---

## 📊 Performance Comparison Table

| Method                  | Total Time (seconds) | Workers/Nodes Used | Speedup |
|--------------------------|----------------------|--------------------|----------|
| Sequential               | 0.55                 | 1 worker           | 1.00x    |
| Parallel (2 workers)     | 1.16                 | 2 workers          | 0.79x    |
| Parallel (4 workers)     | 0.97                 | 4 workers          | 0.94x    |
| Parallel (8 workers)     | 1.63                 | 8 workers          | 0.56x    |
| Distributed (2 nodes)    | 1.20                 | 2 nodes            | 15.19x   |

---

## 🏆 Best Number of Workers
The **best performance** was achieved using **4 workers** in the parallel configuration.  
While increasing workers improved concurrency, beyond 4 workers the overhead from **context switching** and **I/O contention** reduced overall efficiency.  
Hence, 4 workers provided an optimal balance between CPU utilization and task scheduling.

---

## 💬 Discussion
Parallelism improved performance by allowing multiple images to be processed **simultaneously across CPU cores**, effectively reducing total execution time compared to the sequential method.  
However, the speedup was **not linear** due to several **bottlenecks**:

- **I/O operations** (reading and saving images) still occur sequentially and dominate total processing time.  
- The **dataset size is small**, so parallel overhead (process creation, data serialization) can outweigh performance gains.  
- Increasing workers beyond the CPU’s optimal core count leads to **context switching** and **memory contention**.

Future improvements could include:
- Implementing **asynchronous I/O** to reduce file read/write latency.  
- Using **GPU acceleration (CUDA)** for faster image transformations.  
- Employing **batch processing** for better workload distribution.

---

## 👩‍💻 Author
**Wajeeha Aslam**  
BS Computer Science – COMSATS University Lahore  
**Course:** Parallel and Distributed Computing  
**Date:** October 27, 2025

---

