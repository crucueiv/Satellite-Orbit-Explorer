# Satellite Orbit Explorer

A Python notebook that propagates four satellites in different orbital regimes over 24 hours, compares them with tables and plots, and exports the trajectories as KML for Google Earth.

Built during **Space Career Week 2026 (SCW26)**, a free online event by **GNSS Academy**.

**Notebook:** [Open in Google Colab](https://colab.research.google.com/drive/1NO8OTDJR1UuydxkwS8zRfG2vGK7reKMP?usp=sharing)

## What it does

1. Loads orbital elements (CelesTrak-style GP data) for four satellites.
2. Propagates each orbit with an analytical two-body (Keplerian) model.
3. Computes summary statistics: period, perigee/apogee altitude, eccentricity, inclination, min/max speed.
4. Plots ground tracks and speed over time.
5. Exports Earth-fixed trajectories and a time animation as KML.

## Satellites

| Satellite | NORAD | Regime |
|---|---|---|
| PULSAR-0 | 64541 | LEO, near-polar |
| GSAT0225 (Galileo 29) | 59598 | MEO (GNSS) |
| SES-5 | 38652 | GEO |
| QZS-2 (Michibiki-2) | 42738 | IGSO |

## Simulation settings

- Window: 2026-11-10 00:00 UTC to 2026-11-11 00:00 UTC
- Time step: 5 s (17,281 samples per satellite)

## Outputs

| File | Description |
|---|---|
| `ground_tracks.png` | Ground tracks of the four satellites over 24 h |
| `velocity_timeseries.png` | Orbital speed over time, one panel per satellite |
| `orbit_tracks_ecef.kml` | Earth-fixed trajectories, open in Google Earth |
| `orbit_animation.kml` | Time animation of the ground tracks |
| `orbit_report.txt` | Input elements and summary table |

## Key results

- PULSAR-0 completes about 15 orbits per day and reaches about 82.5° latitude.
- SES-5 stays over one point on the equator (geostationary).
- QZS-2 draws a figure-eight ground track and shows the largest speed variation (2.85 to 3.31 km/s) because of its eccentricity (0.0745).
- Galileo 29 (period 14.08 h) completes about 1.7 orbits per day.

## Assumptions and limitations

- **Two-body model:** no J2, drag or solar radiation pressure. Fine for a 24-hour comparison, not for long-term prediction.
- **Mean elements** are used in a propagator that expects osculating elements, which adds a small systematic error.
- **Epoch age:** QZS-2's elements date from 2026-10-17 (about 24 days before the simulation), so its predicted position is less reliable than the others.
- **Spherical Earth approximation** for altitude and ground-track conversion.
- **Data source:** SOURCE_NAME, retrieved 2026-11-10 16:30 UTC.

## How to rerun

1. Open the notebook in Google Colab.
2. Run all cells (`Runtime > Run all`). Fetching external data requires internet access.
3. Download the generated files from the Colab file browser.
4. Open the `.kml` files in Google Earth.

## What I learned

Plotting an orbit is easy. The valuable part is documenting which assumptions the plot depends on, and where the model stops being trustworthy.

## Credits

Built during Space Career Week 2026 (SCW26), a free online event by GNSS Academy.
