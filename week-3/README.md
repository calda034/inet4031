# Week 3, Containerizing the Incident Tracker

## What this does
Packages the Flask incident tracking app into a Docker image and runs it as a container, reachable on port 8080.

## Requirements
- Docker
- A .env file in app/ (copy app/.env.example and fill in FLASK_SECRET_KEY)

## Build and run
cd app
docker build -t incident-tracker:1.0 .
docker run -d -p 8080:5000 --env-file .env --name incident-tracker incident-tracker:1.0

## Verify
curl http://localhost:8080
Or visit http://localhost:8080 in a browser.

## Known limitation
Data does not persist across docker rm, no volume is configured yet.

## Reach it

Inside the VM: http://127.0.0.1:8080

From the Mac: http://192.168.64.10:8080

`localhost:8080` on the Mac reaches the Mac, not the VM. If the Mac address stops working, run `hostname -I` in the VM and use the `192.168.64.x` address with port `8080`.
