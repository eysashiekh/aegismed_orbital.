# AegisMed Orbital

Autonomous crew telemetry and countermeasure system for long-duration spaceflight. Built for the NASA Space Apps Challenge.

- **Live app:** https://aegismedo-orbital.netlify.app/ (add `?tour` to the address to start the guided tour)
- **Demo video:** https://www.loom.com/share/d30f51efdc99405da832969eec30d835

## What it does

AegisMed Orbital is a web dashboard that helps keep astronauts healthy on missions to the Moon and Mars. It shows crew vital signs, warns before a vital leaves its safe range, and connects crew health to live space weather and the real position of the ISS.

**Features**

- Six live vitals per crew member (heart rate, blood pressure, blood glucose, core temperature, sleep, stress), marked Nominal, Warning or Critical, with trend lines
- Autonomous early warning that predicts when a vital will leave its safe range
- Emergency simulator (solar flare, stress spike, fluid shift) with protocols
- Interactive body map, full-screen body scan, live ECG, spacewalk (EVA) readiness check
- Daily countermeasures (exercise timer, hydration, light), health trends, medical supplies, mission log
- Crew management: add, edit and remove crew members
- Flight surgeon chat, printable health report, voice commands, mission control wall mode, guided tour
- Live data: ISS position on a map, solar flares, X-ray and proton radiation levels, Kp index, live Sun images, aurora forecast, Earth images, asteroids, natural events

## Real data and simulated data

| Real | Simulated |
|---|---|
| ISS position, solar flares, space weather, live images, asteroids, natural events, heart rate from a connected Bluetooth sensor | Crew vitals, crew records, medical supplies, accumulated radiation dose |

The health limits in this project are for demonstration only. They are not medical advice.

## Tech stack

- HTML, CSS and JavaScript, with no build step and no framework
- [Three.js](https://threejs.org) (r128) for the 3D Earth and space scene
- [Leaflet](https://leafletjs.com) (1.9.4) for the ISS map, with [CARTO](https://carto.com/basemaps) tiles and OpenStreetMap data
- Google Fonts: Orbitron and Sora
- Browser features: Canvas, SVG, Web Bluetooth, Web Speech, localStorage

## Dependencies

There is nothing to install. The whole app is one file, `index.html`. It loads Three.js and Leaflet from cdnjs and the fonts from Google Fonts, so it needs an internet connection the first time it loads.

## How to run

**Option 1: open the file.** Download `index.html` and open it in a browser.

**Option 2: run a local server (recommended).** From the folder that contains `index.html`:

```
python3 -m http.server 8000
```

Then open http://localhost:8000 in your browser. In Visual Studio Code, the Live Server extension does the same.

**Deploy.** Upload `index.html` to any static host, for example Netlify. Use `https`, because Web Bluetooth needs it.

## Browser support

- Works in current Chrome, Edge, Firefox and Safari, on laptops and phones
- Bluetooth heart-rate sensor and voice commands work in Chrome and Edge only (Android and desktop)

## Optional settings

- **NASA API key:** the asteroid and picture-of-the-day panels use NASA's free `DEMO_KEY`, which has a low request limit. Get a free key at https://api.nasa.gov and paste it in **Settings**.
- **3D quality, accent color, larger text and sound** can be changed in **Settings**.
- Crew, logs and settings are saved in your browser's local storage. **Settings > Reset everything** clears them.

## Data sources and credits

- NASA CCMC DONKI (solar flares): https://ccmc.gsfc.nasa.gov/tools/DONKI
- NASA Solar Dynamics Observatory: https://sdo.gsfc.nasa.gov/
- NASA EPIC: https://epic.gsfc.nasa.gov/
- NASA Open APIs (NeoWs, APOD): https://api.nasa.gov/
- NASA EONET: https://eonet.gsfc.nasa.gov/
- NOAA Space Weather Prediction Center: https://services.swpc.noaa.gov/json/goes/ and https://www.swpc.noaa.gov/noaa-scales-explanation
- Where the ISS at? API: https://wheretheiss.at/w/developer
- NASA Human Research Program: https://www.nasa.gov/hrp/
- NASA Open Science Data Repository: https://osdr.nasa.gov/

We acknowledge the Community Coordinated Modeling Center (CCMC) at Goddard Space Flight Center for the use of DONKI.

Development assistance: the AI assistant Claude (Anthropic) helped write and test the code.
