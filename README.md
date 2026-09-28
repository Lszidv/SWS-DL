# SWS-DL

English | [简体中文](./README_zh-CN.md)

SWS-DL is a Windows desktop application for shear-wave splitting analysis. It provides waveform preprocessing, polarization analysis, particle-motion comparison, result export, and station-based statistics.

## Download

Download the latest Windows package from the [Releases page](../../releases/latest).

After extracting the package, run `SWS-DL.exe`. Keep the `_internal` directory beside the executable.

## Data Requirements

SWS-DL reads three-component SAC waveforms from the same event:

- Vertical: `V` or `Z`
- East-West: `E`
- North-South: `N`

The files should be stored in the same directory and share the same prefix, for example:

```text
event01.V.SAC
event01.E.SAC
event01.N.SAC
```

If the components cannot be identified automatically, the application will ask you to select them manually.

## Analysis Workflow

1. Click **Load SAC Files** and select any one of the three components.
2. Apply filtering, mean removal, or linear detrending when needed.
3. Set the start and end of the analysis window and inspect the selected waveform segment.
4. Search automatically or set the fast polarization direction `φ` manually, then confirm it.
5. Measure automatically or set the delay time `δt` manually, then apply the correction.
6. Inspect the five-component waveforms and the particle-motion plots before and after correction.
7. Export the analysis result.

> Automatic searches are intended to assist manual interpretation. Final results should be reviewed using the waveforms, particle-motion patterns, and relevant research experience.

## Output

Results are saved under the application directory:

```text
results/
├── sws_results.csv
└── STATION/
    ├── event_result.txt
    └── event_result.json
```

Do not change the JSON field structure, as the station statistics module depends on it.

## Station Statistics

- Select the `results` directory to view station averages and fast-direction rose diagrams.
- Select a station directory to view event name, `φ`, `δt`, and quality grade for each event.
- Results can be filtered by quality grade, exported, or saved as rose diagrams.

## Troubleshooting

- **The application does not start:** Ensure the package is fully extracted and `_internal` remains beside `SWS-DL.exe`.
- **Components are not recognized:** Check the file location and naming, or select each component manually.
- **Results cannot be exported:** Confirm the fast direction and apply the delay-time correction first.
- **Station statistics are empty:** Ensure the selected directory contains JSON files exported by SWS-DL.

**System requirement:** Windows 64-bit
