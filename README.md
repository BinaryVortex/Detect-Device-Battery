# Detect Device Battery

Detect Device Battery is a tiny, educational web app built with HTML, CSS, and JavaScript that shows the current battery level and charging status of the user's device using the Battery Status API. It's a simple demo useful for learning how to access battery information in supporting browsers.

![Detect Device Battery screenshot](./Screenshot%202024-04-26%20111615.png)

## Features
- Shows current battery percentage
- Displays whether the device is charging or discharging
- Visual battery indicator and readable status text
- Lightweight: plain HTML/CSS/JavaScript (no frameworks)

## Demo / Screenshot
See the screenshot above for the UI. To try the app locally, follow the steps below.

## How it works
The app uses the browser Battery Status API (navigator.getBattery()) to read battery level and charging status and updates the UI in real time as values change.

Important: the Battery Status API is deprecated or restricted in some browsers for privacy reasons. The app works best in browsers that still expose navigator.getBattery().

## Technologies
- HTML
- CSS
- JavaScript (vanilla)

## Installation / Run locally
1. Clone the repository:
   git clone https://github.com/BinaryVortex/Detect-Device-Battery.git
2. Change into the project directory:
   cd Detect-Device-Battery
3. Open `index.html` in your browser:
   - Directly: double-click `index.html` (may work in many browsers), or
   - Recommended (serves over HTTP): run a simple server and open http://localhost:8000
     - Python 3:
       python -m http.server 8000
     - Node (http-server):
       npx http-server -p 8000

## Usage
- Open the app in a compatible browser.
- If the browser supports the Battery API, the battery percentage and charging state will display and update automatically.
- If the API is unavailable, a friendly message is shown explaining that battery info is not supported.

Example of the core logic (simplified):
```js
if ('getBattery' in navigator) {
  navigator.getBattery().then(battery => {
    function update() {
      const level = Math.round(battery.level * 100);
      const charging = battery.charging ? 'Charging' : 'Not charging';
      // update DOM elements here
    }
    battery.addEventListener('levelchange', update);
    battery.addEventListener('chargingchange', update);
    update();
  });
} else {
  // show fallback / unsupported message
}
