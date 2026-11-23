# Genesis Ultra v1.0.0 🚀

First public release of **Genesis**, an RF network planning and analysis tool for smart meter and gateway deployments. It helps you work out how meters connect to gateways, where new gateways should go, and which nodes can hear each other.

## ✨ What's included

### 🔗 Hop Analysis (core)
- Upload a **gateway CSV** and a **meter CSV** (latitude and longitude), then set your **Hop-1** and **Hop-2** ranges in meters.
- Assigns each meter to its nearest gateway (Hop 1) or to a Hop-1 meter (Hop 2).
- Outputs:
  - a **hop analysis CSV** (hop level, connected gateway, distance)
  - a **gateway summary CSV** (Hop-1 and Hop-2 counts, total hops, total Hop-1 distance per gateway)
  - a **Google Earth KML** network map (green for Hop 1, blue for Hop 2, red for overloaded gateways)
- Coordinates are validated automatically, and invalid rows are saved to a separate CSV with the reason.
- A network statistics window shows hop distribution, coordinate validation and distance analysis.

### 🗺️ MATMAP.io: Gateway Planner
- Suggests optimal gateway locations from unplanned meter locations.
- Uses DBSCAN clustering and K-Means with a 398 m coverage radius per gateway.
- Outputs a gateway summary CSV and a KML file for Google Earth.

### 📡 Earshot.io: Node Proximity Analyzer (new)
- Upload one CSV with lat/long and enter a **Threshold Earshot** in meters (for example 100).
- Finds every node that has at least one other node within that distance.
- Outputs:
  - a **nodes CSV** (neighbour count, nearest node, all neighbours with distances)
  - a **links CSV** (one row per node pair, with distance)
  - a **Google Earth Pro KML** topology with distance-labelled links
- Uses a BallTree radius search with haversine distance, so results are exact and fast on large files.

### 🔄 Built-in update notifications
- Genesis checks this repository on startup and tells you when a new version is available.
- There is also a **Check for updates** button in the footer.

## 📦 Requirements
- Python 3.12 or newer
- Packages:
  ```
  pip install pandas numpy matplotlib scipy scikit-learn simplekml pillow opencv-python requests pygame-ce
  ```
  Use `pygame-ce` instead of `pygame` on newer Python versions.

## ▶️ How to run
```
python Genesis_Ultra.py
```

## 📎 Downloads
- `Genesis_Ultra.py`: the main application

---
Developed by **Arman Mathew**. Questions or feedback: open an issue in this repository.
