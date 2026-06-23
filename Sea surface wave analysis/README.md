# Sea Surface Wind — Sentinel-1 OCN

Visualise sea surface wind speed, wind direction, and radial surface velocity from **Sentinel-1 IW OCN** products using Python.

---

## What this does

Reads the OCN NetCDF file inside a Sentinel-1 `.SAFE` folder and produces three plots:

- **Wind speed** (m/s) with direction arrows
- **Wind direction** (degrees from North)
- **Radial velocity** (m/s) — surface current component toward/away from the satellite

---

## Data

Sentinel-1 **IW OCN** product — download free from:  
👉 [Copernicus Data Space](https://dataspace.copernicus.eu)

Search filters:
- Mission: Sentinel-1
- Product type: OCN
- Mode: IW

After downloading, unzip the `.SAFE` folder and place the main NetCDF file (`s1*-iw-ocn-vv-*.nc`) inside a `data/` folder.

> **Note:** Use the file named `iw-ocn` (not `iw1-osw`, `iw2-osw`, or `iw3-osw` — those contain wave spectra).

---

## Folder structure

```
sea_surface_wind/
├── data/
│   └── s1d-iw-ocn-vv-*.nc       ← your OCN NetCDF file here
├── ocn_wind.ipynb                ← main notebook
├── README.md
└── requirements.txt
```

---

## Requirements

```bash
pip install -r requirements.txt
```

`requirements.txt`:
```
xarray
numpy
matplotlib
h5netcdf
```

---

## How to use

1. Clone the repo and install requirements
2. Place your OCN NetCDF file in the `data/` folder
3. Open `ocn_wind.ipynb`
4. In **Section 1**, update `nc_path` to point to your file
5. Run all cells

---

## Understanding the outputs

| Plot | What it shows |
|------|---------------|
| Wind speed + arrows | Speed in m/s; arrows show where wind is blowing toward |
| Wind direction | Degrees from North (meteorological convention) |
| Radial velocity | Blue = water moving toward satellite; Red = moving away |

Wind direction uses **meteorological convention**: 0° = wind coming from North, 90° = wind coming from East.

---

## Key concepts

**OWI (Ocean Wind field):** derived from Bragg scattering — higher wind roughens the sea surface, increasing sigma0. CMOD5.N GMF is used to invert sigma0 to wind speed.

**RVL (Radial Velocity):** Doppler shift caused by moving ocean surface. Only the line-of-sight (radial) component is measured — not the full 2D current vector.

---

## Author

Sadra Emamalizadeh — June 2026
