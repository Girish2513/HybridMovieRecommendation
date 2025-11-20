# Hybrid Movie Recommendation System

## Overview
This project implements an optimized hybrid movie recommendation system based on weighted classification and user collaborative filtering algorithms. The system combines local K-Means clustering with global nearest neighbor search to provide accurate movie recommendations.

## Features
- **Hybrid Recommendation Approach**: Combines multiple algorithms for better accuracy
  - Local K-Means clustering with Pearson correlation similarity
  - Global nearest neighbor search with weighted threshold
  - User collaborative filtering
- **Sparse Matrix Representation**: Efficient handling of user-movie rating data
- **Performance Metrics**: Calculates Hit Rate (HR) and Average Hit Rate (ARHR) for both local and global methods
- **Interactive GUI**: User-friendly Tkinter-based interface
- **Visualization**: Graphical comparison of HR and ARHR metrics
- **Real-time Predictions**: Get movie recommendations based on user and movie IDs

## Requirements

### Dependencies
- Python 3.x
- tkinter (usually comes with Python)
- numpy
- pandas
- matplotlib
- scikit-learn
- scipy
- pyclustering

### Installation
Install the required dependencies using pip:

```bash
pip install pyclustering
pip install numpy pandas matplotlib scikit-learn scipy
```

Or install from requirements file:
```bash
pip install -r requirements.txt
```

## Dataset
The system uses the MovieLens dataset with three CSV files:

1. **ratings.csv** - User ratings for movies
   - Columns: user_id, movie_id, rating
   - Format: Tab-separated values

2. **movies.csv** - Movie information
   - Columns: movie_id, title, genres
   - Format: Tab-separated values

3. **users.csv** - User information
   - Format: Tab-separated values

Place these files in the `Dataset/` directory before running the application.

## Usage

### Running the Application

**Windows:**
```bash
run.bat
```

**Linux/Mac:**
```bash
python HybridMovieRecommendation.py
```

### Using the GUI

1. **Upload Dataset**: Click "Upload Movielens Dataset" to load the dataset from the Dataset folder

2. **Calculate Sparse Matrix**: Click "Calculate Sparse Linear Model" to:
   - Extract sparse matrix from ratings data
   - Split data into 80% training and 20% testing sets
   - Normalize the features

3. **Run Clustering**: Click "Run Local Clustering Algorithm" to:
   - Apply K-Means clustering with Pearson correlation
   - Calculate local and global hit rates
   - Compute average hit rates

4. **View Comparison**: Click "Comparison Graph" to visualize:
   - Local HR vs ARHR
   - Global HR vs ARHR

5. **Get Recommendations**: 
   - Enter a User ID and Movie ID
   - Click "Run Weighted Classification"
   - View predicted rating and top 10 recommended movies

## Algorithm Details

### Pearson Correlation Similarity
The system uses Pearson correlation to measure similarity between users, implemented as a custom distance metric for K-Means clustering.

### K-Means Clustering
- Uses 5 initial cluster centers
- Applies user-defined Pearson distance metric
- Groups users with similar rating behaviors
- Tolerance: 0.01

### Hybrid Approach
- **Local Method**: Uses K-Means clustering for local hit rate calculation
- **Global Method**: Uses nearest neighbor with weighted threshold for global hit rate
- Combines both methods for optimal recommendations

## Project Structure
```
HybridMovieRecommendation/
│
├── Dataset/
│   ├── ratings.csv          # User ratings data
│   ├── movies.csv           # Movie information
│   └── users.csv            # User information
│
├── HybridMovieRecommendation.py  # Main application file
├── requirements.txt         # Python dependencies
├── run.bat                  # Windows run script
├── SCREENS.docx            # Screenshots documentation
└── README.md               # This file
```

## Performance Metrics

The system evaluates performance using:
- **Hit Rate (HR)**: Proportion of correctly predicted ratings
- **Average Hit Rate (ARHR)**: Normalized hit rate for ranking quality

Both metrics are calculated for:
- **Local clustering**: Using K-Means cluster predictions
- **Global search**: Using nearest neighbor with maximum similarity

## Technical Details

### Data Processing
- Reads 10,000 rows from ratings dataset for efficient processing
- Handles missing values by filling with 0
- Normalizes features using sklearn's normalize function
- Uses tab-separated values (TSV) format with Latin-1 encoding

### Model Training
- 80% data for training
- 20% data for testing
- Normalized sparse matrix as input features
- Rating values as target labels

## Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

## License
This project is open source and available for educational purposes.

## Acknowledgments
- MovieLens dataset providers
- Pyclustering library for K-Means implementation
- Research paper on hybrid recommendation systems
