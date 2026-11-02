# Voz México – station data

The Voz México app reads `stations.json` from this repo
(`https://raw.githubusercontent.com/<user>/radio-mexico-data/main/stations.json`).
Phones pick up changes within an hour (pull to refresh in the app to get them at once).
No app update is needed.

## Add or edit a station

Edit `stations.json` on GitHub (pencil icon) and commit to `main`. Each station is one line:

```json
{"name": "Ke Buena 92.9 FM (CDMX)", "streamUrl": "https://…/KEBUENAAAC.aac", "logoUrl": "https://…/logo.jpg", "genre": "Regional"}
```

- `name` – shown in the app, must be unique.
- `streamUrl` – direct audio link (https preferred). Open it in a browser first: it should play.
- `logoUrl` – square image, https.
- `genre` – one of `Music`, `Regional`, `News`, `Sports`, `General`, `Religious`.
- Order in the file is the order in the app.
- To remove a station, delete its line. Mind the commas: no comma after the last entry.

Don't edit `offline`, `lowStreamUrl` or `bitrate` by hand: the daily check fills them in.

## Daily check

`.github/workflows/check-stations.yml` tests every link each night and commits the result
(offline stations go to the bottom of the list). Run it by hand from the Actions tab.

## Update prompt

`update.json` shows a "new version" dialog in the app: set `"show": true` and
`latestVersionCode` higher than the installed build. `"force": true` removes the Later button.
