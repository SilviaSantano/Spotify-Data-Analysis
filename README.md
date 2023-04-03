# Spotify Data Analysis and Visualization

I created a tool to analyze and visualize my personal Spotify data with a python Jupyter notebook.
It is based on the data extracted from the exported json files that you can request to Spotify: the streaming history (listening data of the last year), your library and the extended streaming history (since the creation of the account) and on further information about tracks and artists that can be collected through the API. 

There is a lot of interesting information, if you know how to dig deep, that can be extracted from this data and a myriad of ways how all this information can be visualized in meaningful ways that give you relevant insights into your tastes and habits. 

The tool can be used without adjustments with the data of any other account.
For the data analysis and manipulation I used common python packages such as pandas and numpy and for the dozens of visualizations, I used plotly, matplotlib, seaborn and wordcloud.

## Visualizations
These are only a few of the visualizations I created.

Based solely on the streaming history, you can create charts showing the amount of time listened to music per day/month/... You can also be more specific, by filtering for a specific feature, for instance a specific artist.
I also created heat maps of the time I listened to music per month, and also classified by hour of the day over time.

![newplot (2)](https://user-images.githubusercontent.com/12804135/229575521-02bffcac-1485-44f3-8d11-1d10bbe51599.png)

Another thing that can be done is extracting the most played artists, which you can display  in any kind of chart using as metric the amount of time listened combined. This will give you an overview of the evolution of your interest in an artist over time. You can also create a wordcloud.

![newplot (7)](https://user-images.githubusercontent.com/12804135/229576297-44920e3e-3eac-4eff-82ef-a239dc42c763.jpg)

Similar analysis can be done for the top songs to discover your true favorites :).

![newplot (6)](https://user-images.githubusercontent.com/12804135/229575665-e21c5898-882d-4dac-8ae9-60e538052334.png)

Using the library, similar visualizations can be created. On top of this, I also created a graph to compare how much of the music I heard was in my library compared to music that was not.

With the extended streaming history, you moreover have the details about the device that it was streamed to, which offers new information about usage that can be displayed. You can visualize what the preferred device is depending on the time of the day or day of the week.

The most interesting part comes when you combine all information you have in the extended streaming history with further properties about the tracks and artists collected via the API. For example, the audio features contain values such as danceability, energy, valence, loudness, instrumentalness, liveness, speechiness and valence of tracks, among others.

<img width="346" alt="Screenshot 2023-04-01 at 02 48 41" src="https://user-images.githubusercontent.com/12804135/229576769-f4c37121-7666-4d11-94d4-bef84d99414e.png"><img width="353" alt="Screenshot 2023-04-01 at 02 48 56" src="https://user-images.githubusercontent.com/12804135/229576770-bb007a4a-de82-47a5-81ce-ac67576bd7a7.png">

You can see how the average audio features over your favorite tracks compare to the current top charts in a radar chart and learn that most current top charts are really danceable.

<img width="779" alt="Screenshot 2023-04-03 at 19 09 06" src="https://user-images.githubusercontent.com/12804135/229580026-3bb033f4-22a6-4e8b-9253-406046d2361a.png">

You can even visualize the relationship between two of these parameters using scatterplots.

<img width="785" alt="Screenshot 2023-04-01 at 02 51 00" src="https://user-images.githubusercontent.com/12804135/229576774-eabc60bd-ac27-4820-8e83-69e4825d0b3e.png">

There is also other musical information such as the key the song is (mostly) in, the tempo and the mode (major/minor).

<img width="773" alt="Screenshot 2023-04-01 at 02 51 32" src="https://user-images.githubusercontent.com/12804135/229576786-8c80c9b9-338c-4eae-b62a-03bcd434f6b2.png">

You can also see the popularity of your favorite tracks and artists and their musical genres.
![newplot (19)](https://user-images.githubusercontent.com/12804135/229576936-4f9cca5a-c621-4201-bda7-3eac440b3d4c.png)


## Personal Data
As per the GDPR every user is allowed to request all data collected about their usage of the software. To request your personal data from Spotify, log in to your account and find the button under privacy settings and you will be informed when it is ready to download around a couple of days later. The zip file you download contains many different files, from which the most relevant in this case are 'StreamingHistory0.json' and 'YourLibrary.json', as they contain the listening history and your library, respectively. 
These files only refer to the past 12 months but you can also request separately your entire history. The process is a bit longer and involves a bit more effort but you will get the full data some days later. 

## API
In order to use the Spotify API, you can log in with your account to the [Developer Dashboard](https://developer.spotify.com/dashboard) to create credentials for authentication by creating an 'app', that will be the client. After that, you can use the client id and secret id in the code to make the requests.

For accessing the API I tried both, using regular requests and the spotipy library and found out that even if the library does work as intended it makes it hard to work with when you are analysing a high amount of data. When a request fails, it does so silently masking the actual HTTP error so I preferred to go for using normal requests to the API instead of the wrapper so I can know immediately if one failed and with what error and abort.

The API is realy powerful and can do way more than what we are using it for here. Explore!

## Usage
Once you got the data, unzip it and move the contents to a new folder named 'data' in the same folder you've downloaded the notebook in.
Edit both 'CLIENT_ID' and 'CLIENT_SECRET' in the code, so that your credentials will be used to create the client that will talk to the Spotify API.
Install the dependencies.
Run the jupyter notebook and have fun!
