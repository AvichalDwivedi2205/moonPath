# Lunar Rover Path Planning and Sunlight Optimization

## Project Overview
This project focuses on developing an optimized path planning solution for a solar-powered lunar rover. The goal is to ensure the rover avoids hazardous craters while maximizing exposure to sunlight for efficient charging.

### Objectives:
- Develop a safe and efficient path planning solution.
- Avoid craters to ensure rover safety.
- Maximize sunlight exposure for optimal charging.

### Key Components:
- **Crater Detection Using Roboflow’s API**
- **A* Search Algorithm for Path Planning**
- **Simulated Sunlight Data Integration**

## Dataset and Crater Detection
### Dataset Details:
- **Name**: Chandrayaan-2 OHRC Lunar Crater Dataset
- **Source**: [Roboflow Universe](https://universe.roboflow.com/titaniumsv5/chandrayaan-2-ohrc-lunar-crater-dataset)

### Crater Detection API:
- **Model**: Lunar Crater Detection 2
- **API Endpoint**: Roboflow API
- **Usage**: Inference on lunar images to identify crater positions and sizes.

## Crater Detection & Image Annotation
### Process Overview:
1. **Image Inference**:
   - Each image is processed using the Roboflow Crater API.
   - API returns bounding boxes, classes, and confidence levels for each crater.
2. **Annotation**:
   - Bounding boxes are drawn on images using OpenCV.
   - Labels (classes and confidence levels) are added for visual confirmation.

### Code Highlights:
- Integration of Inference SDK.
- Processing of training and validation images.
- Saving annotated images for further analysis.

## Rover Path Planning Using A*
### Objective:
- Find a safe path of at least **100 meters** avoiding craters.

### Algorithm Details:
1. **Occupancy Grid**:
   - Derived from crater bounding boxes (blocked regions).
2. **A* Search**:
   - Uses **8-directional** neighbor exploration.
   - Cost function integrates both distance and sunlight penalty.
   - Heuristic is based on the remaining path length.
3. **Path Reconstruction**:
   - Backtracking from the goal to the start to obtain path coordinates.

## Rationale Behind Stop Selection
- The **Moon’s south pole** contains highland and mare regions with diverse mineral compositions.
- Stops at exposed bedrock or fault lines provide insights into lunar crust formation.
- Stops at **transition zones** between sunlit and shadowed regions aid in **thermal and radiation studies** for astronaut safety.
- Unique surface formations may offer natural radiation shielding properties (e.g., **magnetic anomaly sites**).

## Incorporating Sunlight Data
### Sunlight Simulation:
- Convert images to grayscale to simulate sunlight intensity.
- Normalize values (**0 = dark, 1 = bright**).

### Cost Function Modification:
- **Cost = Step Distance + Sunlight Weight × (1 − Sunlight Intensity)**
- This encourages path selection through **brighter regions**.

### Stop Adjustment:
- Candidate stops are adjusted (within a **3m window**) to maximize sunlight exposure.

## Results and Achievements
- Successfully annotated images showing rover paths avoiding craters.
- Stops placed in **high-sunlight regions** for optimal solar charging.
- Best path selected based on the **lowest crater coverage (safety score)**.
- Successful **integration of crater detection and sunlight data**.
- Implementation of **A* path planning** tailored to lunar conditions.
- Links to additional paths and results.

## Links
- **Results and Data**: [Google Drive Folder](https://drive.google.com/drive/folders/1qlwjcchzTUvtpHB-1JPiwtfgYSocVcYq?usp=sharing)

---
### Thank You!
For any inquiries, feel free to check the provided links or contribute to the project. 🚀

