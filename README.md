### SPOTIFY DATA ANALYSIS USING GOOGLE COLAB

# **SPOTIFY DATA ANALYSIS**

---


import seaborn as sn
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import warnings
warnings.filterwarnings('ignore')

data=pd.read_csv('spotify_tracks.csv')
data.head()

#  what are the genres available in dataset

# Get the unique values from the 'genre' column
genres = data['genre'].unique()

# Print the unique genres
print(genres)


# prompt: positive and negative histogram for explict based on genres

import matplotlib.pyplot as plt
import seaborn as sns

explicit_counts = data.groupby('genre')['explicit'].value_counts()

# Create separate DataFrames for explicit and non-explicit tracks
explicit_df = explicit_counts.loc[:, True].reset_index(name='count')
non_explicit_df = explicit_counts.loc[:, False].reset_index(name='count')

# Create two subplots
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(10, 4))

# Plot the histogram for explicit tracks
sns.barplot(x='genre', y='count', data=explicit_df, palette='hls', ax=ax1)
ax1.set_title('Explicit Tracks')
ax1.set_xlabel('Genre')
ax1.set_ylabel('Count')

# Plot the histogram for non-explicit tracks
sns.barplot(x='genre', y='count', data=non_explicit_df, palette='hls', ax=ax2)
ax2.set_title('Non-Explicit Tracks')
ax2.set_xlabel('Genre')
ax2.set_ylabel('Count')

# Show the plot
plt.show()


data.info()

data.describe()

data.isna().mean() #check for null values

Data Explotary

for i in data.columns:
  print(i)


Top 5 most popular artists



top_5_artists=data.groupby('artists')['album'].count().sort_values(ascending=False).head(5)
top_5_artists

top_5_artists.plot.barh()
plt.show()

Top 5 Tracks Duration

long_duration_tracks=data[['album','duration_ms']].sort_values(by="duration_ms",ascending=False)[:5]
long_duration_tracks

plt.figure(figsize=(10,5))
plt.title("Top 5 Tracks Duration")
sn.barplot(y='album',x='duration_ms', data=long_duration_tracks,palette='coolwarm')
plt.show()



data=data.drop(columns="id",axis=1)
data

plt.figure(figsize=(10,5))
plt.title('Distribution of album vs Popularity')
top_10_album=data.groupby('album')['popularity'].mean().sort_values(ascending=False).head(10)
sn.barplot(x=top_10_album.index,y=top_10_album.values,color='r', label='popularity',palette='coolwarm')
plt.xticks(rotation=85, color='b')
plt.xlabel("ALBUM")
plt.ylabel("Popularity")
plt.show()

f={"family":"serif","size":15,"color":"r"}
plt.title("explicit Distribution",fontdict=f)
explicit=data["explicit"].value_counts()
plt.pie(x=explicit,labels=["True","False"],colors=["g","r"],explode=[0.1,0],autopct='%1.1f%%')
plt.show()

plt.figure(figsize=(15,10))
plt.title("Distribution of the popularity")
plt.xlabel("popularity")
plt.ylabel("Count")
sn.histplot(data["popularity"],color="g",bins=30,kde=True,label="popularity")
plt.show()


for col in data.select_dtypes(include="int64").columns:
    sn.displot(data[col],kde=True,color="r",label=col)
    plt.title("Represention of --->>"+col,fontdict=f)

sn.pairplot(data.select_dtypes(include="int64"))

plt.figure(figsize=(15,15))
plt.title("Distribution of album vs. duration_ms",fontdict=f)
top_10_popularity=data.groupby("album")["duration_ms"].mean().sort_values(ascending=True).head(10)
sn.lineplot(x=top_10_popularity.index,y=top_10_popularity.values,color="r",label="duration_ms")
plt.xticks(rotation=45,color="b")
plt.yticks(rotation=90,color="b")
plt.xlabel("Album",fontdict=f)
plt.ylabel("duration_ms",fontdict=f)
plt.show()

f={"family":"serif","size":25,"color":"r"}
plt.title("genre Distribution")
genre=data["genre"].value_counts().head(5)
plt.pie(x=genre,colors=["y","purple","g","r","orange"],labels=["new-age","acoustic","progressive-house","psych-rock","punk"],explode=[0.1,0.1,0.1,0.1,0.1],autopct='%1.1f%%')
plt.show()

data.hist(figsize=(10,10))

calculate correlation

correlation=data.select_dtypes("number").corr()
correlation

spearman=data.select_dtypes("number").corr(method="spearman")
spearman

HEATMAP CORRELATIONAL_MATRIX

plt.figure(figsize=(5,6),dpi=150)
plt.title("Correlation_MAtrix")
sn.heatmap(data.select_dtypes("number").corr(),annot=True,fmt="0.3f",cmap='Blues',linewidths=0.5)
plt.xlabel("Features",fontdict=f)
plt.ylabel("Features",fontdict=f)
plt.xticks(rotation=90,color="b")
plt.yticks(color="b",rotation=90)
plt.show()
