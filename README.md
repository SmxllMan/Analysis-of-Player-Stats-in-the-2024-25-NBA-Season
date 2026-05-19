# Analysis-of-Player-Stats-in-the-2024-25-NBA-Season
Unsupervised clustering of 316 NBA players using K-Means and PCA to discover natural player archetypes and groupings from season performance data.
## Motivation and Context
NBA teams and analysts commonly describe players using informal archetypes — stars, rotation players, big men, bench contributors. But are these groupings actually visible in the numbers, or are they just assumptions?

This project uses unsupervised machine learning to find that answer. By applying K-Means clustering to statistics averages, we let the data reveal whether distinct player types emerge on their own — without any position labels or prior assumptions.

This demonstrates practical application of unsupervised learning to a real-world dataset and the results directly showcases the skill to recognize patterns in high-dimensional data.

## What We Did
- **Source:** NBA - [Player Stats - Season 24/25](https://www.kaggle.com/datasets/eduardopalmieri/nba-player-stats-season-2425) (Listed in the files)
- **Process** Raw game-by-game logs were aggregated into per-player season averages, then filtered by players with at least 10 game and 10 minutes per game
- **Final dataset** 316 players and 5 key features

**Features**
| Feature  | Description |
| ------------- | ------------- |
| PTS | Points per game |
| TRB | Total Rebounds per game |
| AST | Assists per game |
| STL | Steals per game |
| BLK | Blocks per game |

**Algorithms**
- Before clustering, we standardized all features to have a mean of 0 and standard deviation of 1. This is necessary because Points per game (average: 11.6) is measured on a much larger scale than Blocks per game (average: 0.52)
- We applied **PCA** after clustering our data for a 2D visualization

**What We Found**

The elbow plot placed the optimal k at 3-4; we chose k=4 because it aligns with four meaningful NBA archetypes:

| Cluster | Size | Archetype | Key Signal |
| ------------- | ------------- | ------------- | ------------- |
| 0 | 110 players | Rotation players | Near-average across all stats |
| 1 | 117 players | Bench / low-usage contributors | Strongly below average on all features |
| 2 | 50 players | Star guards & playermakers | Highest PTS and AST |
| 3 | 37 players | Defensive big men | Highest TRB and BLK |

## How to Run the Code
1. Download both files and upload to Jupyter or Google Collab  (.csv file into your google drive)
   - Libraries/Imports used: pandas, numpy, matplotlib.pyplot, seaborn.
2. Make sure to change the filepath to your specifications
   - If using Jupyter Cloud, just set path to 'database_24_25.csv'
   - If using Google Collab, add "from google.colab import drive" and "drive.mount('/content/drive', force_remount=True)" to separate lines right below the imports then change the path to '/content/drive/MyDrive/database_24_25.csv'
3. Run the cells in-order and make adjustments to the code to satisfy your curiosity.

## Results and Visualizations
<img width="1548" height="585" alt="image" src="https://github.com/user-attachments/assets/ad0c9266-9d97-45fe-bf05-e1a1e06d509c" />
The left panel shows k-means cluster assignments and the right panel shows points per game overlaid on the same PCA coordinates.
The right panel confirms PC1 correlates strongly with scoring which confirms our conclusion that PC1 correlates to offensive output

## Skills demonstrated
- Python (Pandas, NumPy, Scikit-learn, Matplotlib/Seaborn)
   - data manipulation, analysis, and visualization
   - data aggregation, filtering, and cleaning (groupby, dropna, percentile thresholds)
   -  vector norms, standardization, and linear algebra
   -  KMeans, StandardScaler, and PCA
   -  scatter plots, histograms, elbow curves, and PCA biplots
- Unsupervised learning and statistical analysis
  - K-Means clustering, elbow method for k selection standardization rationale, variance explained, and centroid interpretation
