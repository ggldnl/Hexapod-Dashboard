# Hexapod Dashboard

This repository contains the code for a web-based dashboard to control the robot real-time via WebSocket.

- Use mouse controls to interact with the 3D view:
   - `Left click + drag:` Rotate camera
   - `Right click + drag:` Pan camera
   - `Scroll wheel:` Zoom in/out
- Connect to an Hexapod to receive real-time joint updates.

For a complete overview of the project refer to the [main Hexapod repository](https://github.com/ggldnl/Hexapod.git).

## 🌐 Online viewer

A viewer is accessible [here](https://ggldnl.github.io/projects/hexapod_dashboard/dashboard/index.html) without the need to install anything. The viewer will let you interact with the robot and see it perform some basic animations. With the dashboard you will instead be able to connect to your robot and check its state real time (joint values, battery voltage, ...).

## ⚙️ Setup

The dashboard must be run locally due to browser security restrictions. WebSocket connections require either WSS (secure WebSocket) over HTTPS, or an unsecured WS connection from a local HTTP server. Using tunneling solutions like Cloudflare Tunnel would be required for remote HTTPS deployment, which adds unnecessary complexity.

### Clone or download this repository

```bash
git clone https://github.com/ggldnl/Hexapod-Dashboard
```

### Start a local web server in the project directory:

- Using python:
   ```bash
   # Python 3
   python -m http.server 8000
   
   # Python 2
   python -m SimpleHTTPServer 8000
   ```

- Using Node.js:
   ```bash
   npx http-server -p 8000
   ```

- Using PHP:
   ```bash
   php -S localhost:8000
   ```

### Open your browser and navigate to:
   ```
   http://localhost:8000/dashboard/index.html
   ```

## ℹ️ Expected WebSocket Message Format

```json
{
  "voltage": voltage_value,
  "current": current_value, 
  "joints": {
    "leg_1_coxa": leg_1_coxa_value,
    "leg_1_femur": leg_1_femur_value,
    "leg_1_tibia": leg_1_tibia_value,
    "leg_2_coxa": leg_2_coxa_value,
    ...
  }
}
```

Joint angles should be provided in degrees.

## 🤝 Contribution

Feel free to contribute by opening issues or submitting pull requests. For further information, check out the [main Hexapod repository](https://github.com/ggldnl/Hexapod). Give a ⭐️ to this project if you liked the content.
