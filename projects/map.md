---
layout: project
type: project
image: img/cotton/cotton-square.png
title: "Map"
date: 2023
published: true
labels:
  - Python
  - GitHub
summary: "A map of study abroad options that I developed for exchange program."
---

This is a map I created while researching potential universities for studying abroad. The system retrieves study abroad destinations from a URL and marks them with pins.

To give you a flavor of the code, here is an excerpt from one run:

<hr>

<pre>
import pandas as pd
import folium

df = pd.read_csv("留学先候補一覧.csv",encoding="shift_jis")

univ = df[["緯度","経度","大学名"]].values

m = folium.Map(location=[37.93032099138464, -122.41519319028106],zoom_start=4)

for data in univ:
    folium.Marker([data[0],data[1]],tooltip=data[2]).add_to(m)

m.save("留学先マップ.html") 

</pre>

<hr>
