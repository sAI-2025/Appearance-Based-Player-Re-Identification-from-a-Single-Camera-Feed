#  Appearance-Based Player Re-Identification from a Single Camera Feed

<p align="center">
  <!-- Programming Language & Environment -->
  <img src="https://img.shields.io/badge/Python-3.10-blue?logo=python" alt="Python" />
  <img src="https://img.shields.io/badge/Platform-Linux%2FWindows-lightgrey?logo=windows" alt="Platform" />
  <img src="https://img.shields.io/badge/GPU-Supported-green?logo=nvidia" alt="GPU Support" />
  
  <!-- AI/ML Technologies -->
  <img src="https://img.shields.io/badge/YOLO-Object%20Detection-orange?logo=opencv" alt="YOLO Detection" />
  <img src="https://img.shields.io/badge/Siamese%20Network-PyTorch-9cf?logo=pytorch" alt="Siamese Network" />
  <img src="https://img.shields.io/badge/Similarity-Cosine%20Score-green?logo=scikitlearn" alt="Cosine Similarity" />
  <img src="https://img.shields.io/badge/Matching-Hungarian%20Algorithm-blue?logo=matrix" alt="Hungarian Matching" />
  
  <!-- Project Info -->
  <img src="https://img.shields.io/badge/Status-Prototype-lightgrey?logo=github" alt="Project Status" />
  <img src="https://img.shields.io/badge/License-MIT-green?logo=opensourceinitiative" alt="MIT License" />

  <!-- Notebook or Live Demo -->
  <a href="https://colab.research.google.com/your_notebook_link_here" target="_blank">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open in Colab"/>
  </a>

  <!-- GitHub Socials -->
  <a href="https://github.com/sAI-2025/Cross-Camera-Player-Mapping/stargazers" target="_blank">
    <img src="https://img.shields.io/github/stars/sAI-2025/Cross-Camera-Player-Mapping?style=social" alt="GitHub Stars"/>
  </a>
  <a href="https://github.com/sAI-2025/Cross-Camera-Player-Mapping/issues" target="_blank">
    <img src="https://img.shields.io/github/issues/sAI-2025/Cross-Camera-Player-Mapping?style=social" alt="GitHub Issues"/>
  </a>
</p>

---

## 📌 Project Objective

This project tackles the challenge of **re-identifying football players** in a single video feed using an appearance-based strategy. Even when players temporarily leave the frame, the system ensures they retain the same identity upon re-entry.

---

## 🗂️ Project Structure

```bash
Cross-Camera-Player-Mapping/
│
├── code/
│   ├── titled.ipynb             # Jupyter notebook with full pipeline implementation
│   ├── requirements.txt         # Python dependency list
│
├── results/
│   ├── submit1.mp4              # Annotated result video 1
│   └── submit2.mp4              # Annotated result video 2
│
└── README.md                    # Project documentation (this file)
````

---

## 🚀 Getting Started

### ✅ Prerequisites

Ensure the following tools are installed on your system:

* Python 3.10+
* pip
* Jupyter Notebook
* OpenCV (cv2)
* CUDA (if using GPU)

### 📦 Installation

1. Clone the repository:

```bash
git clone https://github.com/sAI-2025/Appearance-Based-Player-Re-Identification-from-a-Single-Camera-Feed.git
cd Appearance-Based-Player-Re-Identification-from-a-Single-Camera-Feed/code
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

---

## 👩‍💻 Run the Notebook

From the root directory:

```bash
cd code
jupyter notebook titled.ipynb
```

Run all cells to process the video and generate annotated outputs.
Final annotated video is exported to the `results/` folder.
---


## 🧠 How It Works (Methodology)

This system is designed to simulate real-time re-identification. It uses a multi-stage modular pipeline:

### 1.  Player Detection (YOLOv11)

* Pretrained YOLOv11 model detects `player` and `goalkeeper`.
* Filters out ball, referees, and irrelevant classes using confidence thresholding and color heuristics.

### 2.  Initial Identity Assignment

* Unique IDs are assigned to players in the first few seconds.
* Appearance features are extracted and stored as identity references.

### 3.  Appearance Embedding Extraction

A hybrid descriptor is computed using:

* **Color Histograms (HSV)**: capture jersey color.
* **Sobel Texture Filters**: capture logos, numbers, and detail.
* Compared using **cosine similarity** for consistency and accuracy.

### 4.  Frame-by-Frame Tracking

Each new detection is matched to existing tracks using a **multi-metric cost matrix**:

* Centroid distance (Euclidean)
* Appearance similarity (cosine)
* IoU score (overlap)

A greedy assignment algorithm ensures optimal matching.

### 5.  Occlusion Handling & Re-Entries

* Tracks that disappear are timestamped and monitored.
* On reappearance, embeddings are compared to reassign the correct previous ID.

### 6.  Track Management

* Tracks are labeled as `active`, `disappeared`, or `removed`.
* Old tracks are pruned if missing for too long.

### 7.  Visualization & Output

Each frame is annotated with:

* Bounding Boxes
* Unique Player IDs
* Detection Confidence

Final annotated video is exported to the `results/` folder.

---

## ✨ Design Highlights

| Feature                      | Description                                                                |
| ---------------------------- | -------------------------------------------------------------------------- |
| **Re-Identification Logic**  | Maintains IDs across disappearances and occlusions                         |
| **Color + Texture Matching** | Improves robustness over plain color matching                              |
| **Multi-Metric Tracking**    | Combines spatial and appearance cues for more accurate matching            |
| **Smart Filtering**          | Prevents tracking referees or misclassified players using color heuristics |

---

## 📽️ Output Results

Annotated videos are saved in the `results/` directory:

* `submit1.mp4` — Demonstration of ID re-assignment and consistent tracking
* `submit2.mp4` — (Optional) Alternate test case or variation

---




## Contributing

We welcome contributions from the community! To contribute:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/new-feature`
3. Commit your changes: `git commit -m 'Add new feature'`
4. Push to your branch: `git push origin feature/new-feature`
5. Open a Pull Request

---

## 📄 License

Licensed under the **MIT License**. See [LICENSE](./LICENSE) for more.

---


## 📬 Contact & Support

* **GitHub Issues**: [Submit bugs or requests](https://github.com/sAI-2025/Appearance-Based-Player-Re-Identification-from-a-Single-Camera-Feed/issues)
* **Author**: **Sai Krishna Chowdary Chundru**
* **GitHub**: [sAI-2025](https://github.com/sAI-2025)
* **LinkedIn**: [linkedin/sai-krishna-chowdary-chundru](https://linkedin.com/in/sai-krishna-chowdary-chundru)
* **Medium**: [@sai2025](https://medium.com/@sai2025)
---

### Author: Sai Krishna Chowdary Chundru

* **Email**: cchsaikrishnachowdary@gmail.com
* **LinkedIn**: [sai-krishna-chowdary-chundru](https://linkedin.com/in/sai-krishna-chowdary-chundru)

---
