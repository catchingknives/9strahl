# 9strahl

A directional compass showing your proximity to all 9 Berlin U-Bahn lines. Click anywhere on the map to see which lines are nearest and in what direction.

*"Neunstrahl" = "Nine Ray" in German — one spike for each U-Bahn line.*

**Live:** [catchingknives.github.io/9strahl](https://catchingknives.github.io/9strahl/)

## How It Works

### The Compass

Each spike on the compass represents one U-Bahn line:
- **Direction**: Points toward the nearest station of that line
- **Length**: Longer = closer (inverse distance scaling)
- **Color**: Official BVG line colors

### Algorithm

1. For each of the 9 U-Bahn lines, find the closest station
2. Calculate the bearing (compass direction) from your click to that station
3. Calculate spike length using inverse distance: closer stations get longer spikes
4. Render spikes sorted by distance (closest on top) so nearby lines remain visible

### Edge Case: U1/U3 Shared Section

U1 and U3 share the same track between **Wittenbergplatz** and **Warschauer Straße**. To avoid counting this section twice (which would unfairly weight central Kreuzberg), these shared stations are attributed to **U1 only**. U3's unique section runs southwest from Wittenbergplatz to Krumme Lanke.

## Data

- ~175 stations with real geographic coordinates
- 9 U-Bahn lines (U1–U9)
- Station data sourced from OpenStreetMap

## Tech Stack

- Vanilla JavaScript (no frameworks)
- [Leaflet.js](https://leafletjs.com/) for maps
- [CartoDB](https://carto.com/) light tiles
- SVG for compass rendering

## Run Locally

```bash
python3 -m http.server 8080
# Open http://localhost:8080
```

## License

MIT
