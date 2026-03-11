# QR Code Generator Application

A Dockerized Python application that generates QR codes from URLs.

## Author
- **Name:** Krupaa Dulobo
- **Email:** kd495@njit.edu
- **GitHub:** [kd495-stack](https://github.com/kd495-stack)

## DockerHub
- **Image:** [kdulobo12/qr-code-generator-app](https://hub.docker.com/r/kdulobo12/qr-code-generator-app)

## Project Structure
```
qr-code-generator/
├── main.py              # Main application script
├── requirements.txt     # Python dependencies
├── Dockerfile           # Docker configuration
├── .github/
│   └── workflows/
│       └── docker.yml   # GitHub Actions workflow
├── logs/                # Application logs
└── qr_codes/            # Generated QR code images


## How to Build and Run

### Build the Docker Image
```bash
docker build -t qr-code-generator-app .
```

### Run the Container
```bash
docker run -d --name qr-generator \
-v "$(pwd)/qr_codes:/app/qr_codes" \
qr-code-generator-app --url http://github.com/kd495-stack
```

### View Logs
```bash
docker logs qr-generator
```

### Run with a Custom URL
```bash
docker run -d --name qr-generator \
-v "$(pwd)/qr_codes:/app/qr_codes" \
qr-code-generator-app --url http://www.njit.edu
```

### Stop and Remove Container
```bash
docker stop qr-generator
docker rm qr-generator
```

## Security Features
- **Non-Root User:** App runs as `myuser` instead of root
- **Minimal Base Image:** Uses `python:3.12-slim-bullseye`
- **Directory Ownership:** Only `myuser` can write to logs and qr_codes

## GitHub Actions
Automatically builds and pushes the Docker image to DockerHub on every push to `main`.

## Dependencies
- Python 3.12
- qrcode==7.4.2
- Pillow==10.2.0