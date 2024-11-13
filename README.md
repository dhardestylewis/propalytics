# Propalytics

An interactive heat map service providing real estate development financial performance under your belief of the future.

## Overview

Propalytics aims to improve a real estate investor's baseline alpha from the outset by **valuing and visualizing entire markets**. We predictably rank-order properties so that investors and developers can invest confidently, regardless of market conditions, and sleep well knowing they started their property investment search with the top-performing properties.

## Features

- **Interactive Financial Heat Map:** Visualize financial performance metrics like Internal Rate of Return (IRR) and Equity Multiple (EqMult) across entire markets down to individual properties.
- **Client-Controlled Market Scenarios:** Adjust future market scenario sliders to refine asset classes based on your beliefs about key market factors.
- **Statistical Clustering:** Utilize advanced machine learning algorithms to cluster properties into refined asset classes for accurate comparisons.

## Product Visualization

Imagine an interactive heat map similar to topographical maps, but instead of elevation, each area is colored based on financial performance indicators like IRR or EqMult.

![Financial Heat Map](path_to_heat_map_image)

*Visualize IRR and/or EqMult on a web portal like this instead of topography.*

## Business Model

- **Subscription-Based:** Subscriptions support the technical operation of the platform.
- **Profit Sharing:** In exchange for the alpha provided, we take a 2-5% cut of the future earnings from the real estate development (i.e., the promote).

## Target Audience

Investors, developers, and others looking for initial scoping, actual property leads, or a gut-check of properties and their rolled-up submarkets based on financial performance.

## Market Opportunity

- **Rapid Growth:** The proptech space is rapidly growing and is nowhere near mature compared to other VC tech spaces.
- **Largest Asset Class:** Property is the largest asset class in the US, leaving significant room for innovation.

## Competitors

- **Zillow, CompStak, CoStar:** While these companies have internal models, they lack productization for the broader market. Their business models disincentivize them from sharing their alpha.
- **Specialist Firms:** Some specialist firms attempt to productize similar models, but the market is vast enough to outcompete them with the right team.

## Technical Implementation

Our technical solution involves building refined asset classes, collecting future market scenarios, and applying these scenarios to rank properties based on financial performance.

### Key Steps

1. **Building Refined Asset Classes:**
   - **Objective:** Cluster low-density buildings into refined asset classes that serve as representative properties and sets of property comparables.
   - **Implementation:** Advanced machine learning algorithms optimized using metrics like Silhouette Score, Davies-Bouldin Index, Calinski-Harabasz Index, and Gap Statistic.

2. **Gathering Future Market Scenarios:**
   - **Methods:**
     - **Manual Curation:** Analysts manually gather data.
     - **Data Acquisition:** Purchase from major data providers or scrape market reports.
     - **Client Input:** Clients adjust sliders in the web portal based on their beliefs.

3. **Applying Scenarios to Asset Classes:**
   - **Objective:** Sample refined asset class clusters against future market scenarios to build rank-ordering of financial return curves.
   - **Outcome:** Generates the heat map from individual properties up to the entire market.

### Clustering Algorithm

The clustering algorithm ensures well-clustered building typologies by optimizing multiple statistical metrics.

#### Features Used:

- **Regulatory:**
  - Floor Area Ratio (FAR)
  - Maximum height
- **Existing Building:**
  - Existing square footage
  - Height
- **Spatial:**
  - Latitude
  - Longitude

#### Sample Clustering Statistics:

- **Silhouette Score:** 0.2481 (Target > 0.5)
- **Davies-Bouldin Index:** 1.1987 (Target < 1)
- **Calinski-Harabasz Index:** 1323.9118 (Target > 1000)
- **Gap Statistic:** 1.7327 (Target > 1)

### Code Implementation

The clustering algorithm is implemented in Python using libraries like `numpy`, `scikit-learn`, and `psutil`.

#### Sample Code Snippet

```python
import numpy as np
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
import psutil
from sklearn.cluster import MiniBatchKMeans
from sklearn.metrics import silhouette_score, davies_bouldin_score, calinski_harabasz_score
from scipy.stats import f_oneway
import warnings
import time
from concurrent.futures import ThreadPoolExecutor, as_completed
import concurrent.futures
from concurrent.futures import ProcessPoolExecutor
import sys

warnings.filterwarnings('ignore')

# List of relevant features for scaling
features = [
    'LotArea', 'proposed_floor_area',
    'max_height', 'LotFront', 'LotDepth', 'Block', 'max_floors', 'max_floors_current',
    'max_residential_far_current', 'min_front_yard_depth_current', 'min_rear_yard_depth_current',
    'min_side_yard_width_current', 'max_building_height_current',
    'max_residential_far_proposed', 'min_front_yard_depth_proposed', 'min_rear_yard_depth_proposed',
    'min_side_yard_width_proposed', 'max_building_height_proposed'
]

# Function to evaluate cluster metrics
def evaluate_cluster_metrics(X_scaled_df, labels):
    silhouette_avg = silhouette_score(X_scaled_df, labels)
    davies_bouldin_avg = davies_bouldin_score(X_scaled_df, labels)
    calinski_harabasz_avg = calinski_harabasz_score(X_scaled_df, labels)
    return silhouette_avg, davies_bouldin_avg, calinski_harabasz_avg

# ... (additional code)
```

For the complete code, please refer to the `clustering_algorithm.py` file.

## Getting Started

### Prerequisites

- Python 3.7 or higher
- Required Python libraries:
  - `numpy`
  - `scikit-learn`
  - `psutil`
  - `scipy`
  - `warnings`
  - `concurrent.futures`

### Installation

Clone the repository and install the required packages:

```bash
git clone https://github.com/yourusername/propalytics.git
cd propalytics
pip install -r requirements.txt
```

### Usage

To run the clustering algorithm:

```bash
python clustering_algorithm.py
```

## Roadmap

- **Scaling:** Apply the model to other geographic areas and varying market scenarios.
- **Client Onboarding:** Provide free initial access to the web portal for feedback.
- **Continuous Feedback:** Gather insights from VCs, real estate attorneys, developers, and analysts.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.

## License

This project is licensed under the MIT License.

## Contact

Daniel Hardesty Lewis  
Email: [youremail@example.com](mailto:youremail@example.com)  
Affiliations:
- NSF Big10
- TOP500 Supercomputing
- UT Austin Moonshot Initiatives
- Bagnold Medal Contributor

---
