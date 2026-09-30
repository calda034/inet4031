# INET4031

Santiago Caldas Quiroga, INET 4031 (001), Fall 2026.

This is the semester repo for the systems course. Each week gets its own folder. The remote is [calda034/inet4031](https://github.com/calda034/inet4031).

## week-3

`week-3/app` is the Flask incident tracker, built and run as the `incident-tracker` image. The real key stays in `week-3/app/.env` and is not committed. Copy `.env.example` and fill that in locally before starting the container.

## Reach the week-3 app

Inside the VM: http://127.0.0.1:8080

From the Mac: http://192.168.64.10:8080

`localhost:8080` on the Mac reaches the Mac, not the VM. If the Mac address stops working, run `hostname -I` in the VM and use the `192.168.64.x` address with port `8080`.
