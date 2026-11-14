# Historical Weather Explorer

A static Mapbox-based website for choosing a location and retrieving historical daily weather from an existing PythonAnywhere gridMET API.

## Publish with GitHub Pages

In **Settings → Pages → Build and deployment**, choose **Deploy from a branch**, branch **main**, folder **/ (root)**.

Expected URL: https://will-n.github.io/historical-weather-explorer/

## Mapbox token

The public Mapbox token was deliberately **not committed**: GitHub secret scanning blocked the push even though this is a browser-side public token. Set the `MAPBOX_PUBLIC_TOKEN` constant in `index.html` to a Mapbox public (`pk.`) token using an approved configuration method. If GitHub requests push-protection approval, review and authorize its inclusion for this repository through GitHub's documented flow. The owner's screenshot already lists `https://will-n.github.io` as an allowed Mapbox origin.

## Weather API

GET https://weather-bnorthcott1967.pythonanywhere.com/data with `start_date` and `end_date` formatted `MM/DD/YYYY`, `latitude`, `longitude`, and `format=json`.

API response fields are `Date`, `Max Temp`, `Min Temp`, `Rainfall`, and `PET`. Temperatures are in Fahrenheit, rainfall and PET in inches.

## Required PythonAnywhere CORS update

Do **not** commit `Weather_API.py` or NetCDF files here. In the PythonAnywhere server file `/home/bnorthcott1967/weather/Weather_API.py`, set the allowed origins for `/data` to include both `https://www.billsbeeproject.com` and `https://will-n.github.io`, then reload the PythonAnywhere web app.

## Verify

Once Pages is enabled, token configured, and PythonAnywhere reloaded: open the public URL, select a location, choose a short past date range, and confirm five weather columns populate. Use the browser Network tab to check CORS errors if necessary.
