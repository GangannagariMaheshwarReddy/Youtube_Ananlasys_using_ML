# YouTube Data Analysis Project

## Project Overview

This project uses the YouTube Data API v3 along with Python libraries such as Pandas, Matplotlib, and Seaborn to collect, analyze, and visualize YouTube channel and video data.

The project extracts:

* Channel statistics
* Video details
* Playlist information
* Monthly upload analysis
* Views, likes, and comments statistics

The collected data is converted into Pandas DataFrames for analysis and visualization.

---

# Technologies Used

* Python
* YouTube Data API v3
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Google API Client
* Jupyter Notebook / Google Colab

---

# Features

## Channel Analysis

* Fetch channel names
* Fetch subscriber counts
* Fetch total views
* Fetch total videos
* Fetch upload playlist IDs

## Video Analysis

* Extract video IDs from playlists
* Fetch video titles
* Published dates
* Views count
* Likes count
* Comments count

## Data Visualization

* Bar plots
* Monthly upload analysis
* Most viewed videos
* Likes vs Views analysis

---

# Project Structure

```bash
YouTube-Data-Analysis/
│
├── youtube_analysis.ipynb
├── README.md
├── requirements.txt
└── images/
```

---

# Installation

## Clone the Repository

```bash
git clone https://github.com/your-username/YouTube-Data-Analysis.git
```

## Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn google-api-python-client
```

---

# YouTube API Setup

1. Go to Google Cloud Console
2. Create a new project
3. Enable YouTube Data API v3
4. Generate API Key
5. Replace your API key in the project

Example:

```python
api_key = "YOUR_API_KEY"
```

---

# Sample Functions

## Get Channel Statistics

```python
def get_channel_stat(youtube, channel_ids):
    all_data = []

    request = youtube.channels().list(
        part='snippet,contentDetails,statistics',
        id=','.join(channel_ids)
    )

    response = request.execute()

    for i in range(len(response['items'])):
        data = dict(
            Channel_name=response['items'][i]['snippet']['title'],
            Subscribers=response['items'][i]['statistics']['subscriberCount'],
            Views=response['items'][i]['statistics']['viewCount'],
            Total_Videos=response['items'][i]['statistics']['videoCount'],
            Playlist_id=response['items'][i]['contentDetails']['relatedPlaylists']['uploads']
        )

        all_data.append(data)

    return all_data
```

---

# Data Visualization Example

```python
ax2 = sns.barplot(
    x='Month',
    y='size',
    data=video_per_month,
    palette='viridis'
)
```

---

# Output Examples

* Channel subscriber comparison
* Video engagement analysis
* Monthly upload trends
* Top viewed videos
* Likes and comments analysis

---

# Future Enhancements

* Sentiment Analysis on comments
* Streamlit dashboard deployment
* Real-time analytics dashboard
* Machine Learning prediction models
* Export reports to Excel/PDF

---

# Learning Outcomes

Through this project, you will learn:

* Working with APIs
* Data collection and preprocessing
* Data visualization techniques
* Exploratory Data Analysis (EDA)
* Python automation
* Handling JSON responses

---

# Author

Mahi Reddy

---

# License

This project is for educational and learning purposes.
