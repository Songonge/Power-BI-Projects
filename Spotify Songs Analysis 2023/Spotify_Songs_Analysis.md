# Project: Spotify Songs Analysis 2023

## Table of Contents  
1. [Introduction](#introduction)
   * [Business Overview or Problem](#business-overview-or-problem)
   * [Rationale for the Project](#rationale-for-the-project)
2. [Aim of the Project](#aim-of-the-project)
3. [Data Description](#data-description)
4. [Tech Stack](#tech-stack)
5. [Project Scope](#project-scope)
   * [Data Gathering and Integration](#data-gathering-and-integration)
   * [Data Cleaning](#data-cleaning)
   * [Data Analysis and Dashboard Development](#data-analysis-and-dashboard-development)
6. [Data Interpretation](#data-interpretation)
7. [Recommendations](#recommendations)

## Introduction 
This project is the second one completed during my internship at CognoRise Infotech. The project provides an analysis of Spotify songs for the year 2023. The dataset includes famous songs listed on Spotify and describes each song's popularity and attributes on different music platforms.
This project was completed in Power BI where I designed an interactive dashboard to communicate insights from the analysis. 

### Business Overview or Problem
This project leverages Power BI to analyze Spotify song data, providing insights into trends, listener preferences, and genre popularity. By visualizing metrics such as streaming counts and song characteristics, this analysis helps music curators, marketing teams, and artists make data-driven decisions. The goal is to optimize playlist recommendations, target specific audience segments, and enhance user engagement on the platform. Additionally, it supports predictive analysis for emerging artists or trends, allowing Spotify to remain competitive in the digital music landscape.
The key obstacles that could arise include:
1. **Data Availability and Access**: Ensuring access to accurate, real-time Spotify song data might be challenging due to API limitations or licensing restrictions.
2. **Data Quality and Completeness**: Incomplete or inconsistent data, such as missing song features or listener demographic details, could affect the accuracy of insights.
3. **Dynamic User Preferences**: Music trends and user behavior change frequently, making it difficult to keep the analysis relevant and up-to-date without continuous data refreshes.

### Rationale for the Project
The rationale behind the Spotify songs analysis project centers around the need to understand user behavior, enhance product offerings, and make data-driven decisions for business growth.
1. **Enhance User Engagement**: Gain insights into listener preferences to tailor personalized music recommendations and improve user satisfaction on the platform.
2. **Identify Popular Trends**: Analyze streaming patterns to detect emerging music genres, popular artists, and hit songs, allowing for timely content curation.
3. **Support Data-Driven Decisions**: Provide Spotify's marketing and product teams with actionable insights to drive targeted campaigns and improve customer retention.
4. **Optimize Playlist Creation**: Use song characteristics data such as energy, danceability, and liveness to curate more engaging and relevant playlists for different user segments.
5. **Monetize Listener Preferences**: Help Spotify maximize revenue by analyzing which types of content or artists are most popular with different demographic groups, allowing for better advertising or subscription targeting.

## Aim of the Project
The key tasks in this project are to understand what are the top songs and artists on Spotify content and provide recommendations regarding user preferences. Some specific objectives are: 
1. Exploring patterns in audio features to understand trends and preferences in popular songs.
2. Comparing the song's popularity across different music platforms such as Apple, Deezer, and Shazam.
3. Analyzing how artist involvement and attributes relate to a song's success.
4. Identifying any shifts in music attributes and preferences over time.
5. Investigating how songs perform across different streaming services.
 
## Data Description
This dataset consists of information such as track name, artist name, release date, Spotify playlists and charts, streaming statistics, Apple Music presence, Deezer presence, Shazam charts, and various audio features. The dataset contains 24 columns and 953 rows described as follows:
*	*Track Name*: Name of the song
*	*Artist Name*: Name of the artist who sang the song
*	*Artist Count*: Number of artists contributing to the song
*	*Released Year*: The year when the song was released
*	*Released Month*: The month when the song was released
*	*Released Day*: The day when the song was released
*	*Spotify Playlists*: Number of Spotify playlists the song is included in
*	*Spotify Pharts*: Presence and rank of the song on Spotify charts
*	*Streams*: Total number of streams on Spotify
*	*Apple Playlists*: Number of Apple Music playlists the song is included in
*	*Apple Charts*: Presence and rank of the song on Apple Music charts
*	*Deezer Playlists*: Number of Deezer playlists the song is included in
*	*deezer_charts*: Presence and rank of the song on Deezer charts
*	*Shazam Charts*: Presence and rank of the song on Shazam charts
*	*BPM*: Beats per minute, a measure of song tempo
*	*Key*: Key of the song
*	*Mode*: Mode of the song (major or minor)
*	*Danceability*: Percentage indicating how suitable the song is for dancing
*	*Valence*: Positivity of the song's musical content
*	*Energy*: Perceived energy level of the song
*	*Acoustic*: Amount of acoustic sound in the song
*	*Instrumental*: Amount of instrumental content in the song
*	*Live*: Presence of live performance elements
*	*Speech*: Amount of spoken words in the song

## Tech Stack
The analysis tool for this project focused on data analysis using Microsoft Power BI. Therefore, Power BI's built-in features were used to analyze data and design an interactive dashboard.

## Project Scope
To complete this project, several steps were followed such as data gathering, data cleaning, data analysis, and dashboard development.

### Data Gathering and Integration
  1. Download Spotify Songs content from Kaggle.
  2. Store the data in a secure folder for further steps.

### Data Cleaning
Power Query was used to clean and transform the data. To complete this process, I
1. Connected to the data using the Get data feature in Power BI
2. Renamed fields for consistency.
3. Checked for nulls across all columns and replaced them with 0.
4. Replaced empty values with "Not Given" where necessary.
5. Removed the Error value in the Stream column by replacing it with the mean of the column.

### Data Analysis and Dashboard Development
1. I created several charts such as
   * Bar charts to show artists and tracks by the number of streams and artists by tracks
   * A Line chart to show charts from various music platforms by track name
   * A donut chart to show the number of tracks by mode
   * A column chart to show the number of streams by released month
   * A Stacked Bar chart to show the top 10 track names by categories.
2. Designed a dashboard in Power BI to provide an overview of content.
3. Included key metrics and charts to monitor top songs, top tracks, number of streams, and Number of tracks. 
4. After creating all the charts, I combined them in a dashboard as shown in Figure 1.

<figure>
  <img src="https://github.com/Songonge/CognoRise-Infotech/blob/main/Spotify Project/Spotify Dashboard.png" width=100% height=100% alt="alt text">
  <figcaption>Figure: Spotify Songs Analysis 2023 Dashboard</figcaption>
</figure>
<br/><br/>

## Data Interpretation
1. **Top Artists**
   * Artists such as Taylor Swift, The Weeknd, Ed Sheeran, Bad Bunny, and Harry Styles are key figures in terms of streaming numbers and playlist inclusions.
   * Taylor Swift stands out in terms of track followed by The Weeknd, Bad Bunny, and SZA.
2. **Genre and Mood Trends**
   * Major key songs are dominant, indicating a preference for uplifting or conventional sounds.
   * High danceability scores suggest that listeners are drawn to rhythmically engaging tracks.
   * Valence and energy are high across many popular songs, showing that energetic and upbeat tracks are well-received.
3. **Song Characteristics and Engagement**
   * Songs with lower danceability, energy, and valence can still perform exceptionally well such as the one by Olivia Rodrigo.
   * Instrumental is generally low across top tracks, indicating a focus on vocal-led songs.
4. **Release Timing**
   * Songs like "LALA" by Myke Towers and "WHERE SHE GOES" by Bad Bunny, are trending heavily with millions of streams, indicating a rapid rise in popularity post-release.
   * A surge in releases during specific months such as January and May shows strategic timing for song release.
   * The lower amount of releases during other months shows that this is the period when various music platform must advertise their content to boost listener attraction.

## Recommendations
The following recommendations can drive improved engagement and strategic content planning for Spotify and music marketers. This will help curate playlists that match listener preferences and increase streaming numbers.
1. **For Playlist Curation**
   * Prioritize major key and high-energy tracks for general playlists, as these attributes correlate with higher streaming numbers and listener engagement.
   * Create specialized playlists around emotional songs with lower valence and energy to cater to listeners seeking more contemplative or moody music.
2. **Release Strategy**
   * Release new tracks during high-traffic months such as January, March, May, and June when streaming surges, capitalizing on audience activity during holidays or summer.
   * Release new tracks in the summer months when people are on holiday to enhance satisfaction.
3. **Audience Engagement**
   * Promote songs with high danceability and energy during periods associated with high activity, such as parties or events, to drive streams.
   * Explore creating viral dance challenges or campaigns for high-danceability tracks to increase social media exposure and streaming.
4. **Diversity in Musical Offerings**
   * While upbeat tracks dominate, there is a market for more emotionally nuanced or acoustic songs. Consider balancing playlists with both energetic and slower, more emotional tracks to capture a wider audience.  
     
<br/>
   
**Thank you for taking the time to read this report!**

**Please reach out for any updates.**

### Author
[Edwige Songong](https://github.com/Songonge)
