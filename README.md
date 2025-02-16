Slide 1: Title & Overview
Title: Lunar Rover Path Planning: Crater Avoidance & Sunlight Optimization
Subtitle: Using Chandrayaan 2 OHRC Lunar Crater Dataset & Roboflow’s Crater Detection API
Content:
•	Project Aim:
o	Develop a path planning solution for a solar-powered lunar rover.
o	Avoid hazardous craters while maximizing exposure to sunlight for charging.
•	Key Components:
o	Crater detection using Roboflow’s API
o	A* search algorithm for path planning
o	Incorporation of simulated sunlight data
Speaker Notes:
Introduce the project’s goals and explain the importance of both crater avoidance and sunlight optimization in planning safe, efficient rover paths on the lunar surface.
________________________________________
Slide 2: Dataset & Crater Detection API
Title: Dataset & Crater Detection
Content:
•	Dataset Details:
o	Name: Chandrayaan 2 OHRC Lunar Crater Dataset
o	Source: Roboflow Universe
o	Content: High-resolution lunar images with annotated craters.
•	Crater Detection API:
o	Model: Lunar Crater Detection 2
o	API Endpoint: Roboflow API
o	Usage: Inference on lunar images to identify crater positions and sizes.
Speaker Notes:
Explain the importance of the dataset for authentic lunar imagery and how the detection API is used to automatically identify craters, forming the basis for our occupancy grid in the path planning algorithm.
________________________________________
Slide 3: Crater Detection & Image Annotation
Title: Crater Detection and Image Annotation
Content:
•	Process Overview:
o	Image Inference:
	Each image is processed using the Roboflow crater detection API.
	API returns bounding boxes, class, and confidence for each crater.
o	Annotation:
	Bounding boxes drawn on the image using OpenCV.
	Labels (class & confidence) added for visual confirmation.
•	Code Highlights:
o	Inference SDK integration
o	Looping over train and validation images
o	Saving annotated images for further analysis.
Speaker Notes:
Discuss how the code leverages the detection API to annotate lunar images. Emphasize the role of these annotations in creating an occupancy grid, which will later inform the A* path planning algorithm.
________________________________________
Slide 4: Rover Path Planning using A*
Title: Rover Path Planning: A* Algorithm
Content:
•	Path Planning Objective:
o	Find a safe path of ≥ 100 meters avoiding crater areas.
•	Algorithm Details:
o	Occupancy Grid:
	Derived from crater bounding boxes (blocked regions).
o	A Search:*
	Uses 8-directional neighbor exploration.
	Cost function integrates distance and sunlight penalty.
	Heuristic based on remaining path length.
o	Reconstruction:
	Backtracking from goal to start to obtain path coordinates.
•	Output:
o	Annotated path overlaid on the image.
o	Stops placed along the path.
Speaker Notes:
Explain the fundamentals of the A* algorithm and how it’s tailored here: an occupancy grid is used to mark hazardous crater regions, and the search is constrained to find a path of a set length while optimizing for sunlight.
________________________________________
Slide 5: Incorporating Sunlight Data
Title: Enhancing Path Planning with Sunlight Data
Content:
•	Motivation:
o	The rover is solar-powered and needs optimal charging stops.
•	Sunlight Simulation:
o	Sunlight Map Creation:
	Convert images to grayscale to simulate brightness.
	Normalize values (0 = dark, 1 = bright).
•	Cost Function Modification:
o	Add a sunlight penalty term to A* cost:
	Cost=Step Distance+Sunlight Weight×(1−Sunlight Intensity)\text{Cost} = \text{Step Distance} + \text{Sunlight Weight} \times (1 - \text{Sunlight Intensity})Cost=Step Distance+Sunlight Weight×(1−Sunlight Intensity)
o	Encourages path selection through brighter regions.
•	Stop Adjustment:
o	Candidate stops are adjusted locally (within a 3-pixel window) to maximize sunlight exposure.
Speaker Notes:
Detail how simulated sunlight data (derived from image brightness) is integrated into the planning algorithm. Highlight that this adjustment ensures that each stop along the rover’s path is placed in a location optimal for solar charging.
________________________________________
Slide 6: Results & Conclusions
Title: Results, Analysis & Future Directions
Content:
•	Output Results:
o	Annotated images showing rover paths that avoid craters.
o	Stops placed in high-sunlight regions for optimal solar charging.
o	Best path selected based on lowest crater coverage (safety score).
•	Key Achievements:
o	Successful integration of crater detection and sunlight data.
o	Implementation of A* path planning tailored to lunar conditions.
•	Future Work:
o	Incorporate real-time illumination data.
o	Optimize sunlight weighting and stop adjustment parameters.
o	Explore additional environmental constraints.
Speaker Notes:
Summarize the project’s outcomes, emphasizing how the integration of crater detection and simulated sunlight data leads to safer and more efficient rover path planning. Discuss potential improvements and further research directions.
________________________________________
