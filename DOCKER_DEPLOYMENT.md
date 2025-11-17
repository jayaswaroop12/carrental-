# Docker Deployment Guide for Car Rental Frontend

## Prerequisites
- Docker Desktop installed and running
- Docker Hub account with username: `jayaswaroop12`
- Git installed

## Building and Pushing to Docker Hub

### Step 1: Ensure Docker Desktop is Running
Start Docker Desktop on your system. You can verify it's running by opening PowerShell and running:
```bash
docker --version
```

### Step 2: Build the Docker Image
Navigate to the project directory and build the image:
```bash
cd carrental-frontend-main
docker build -t jayaswaroop12/carrental:latest .
```

### Step 3: Login to Docker Hub
```bash
docker login
```
When prompted, enter your Docker Hub username (`jayaswaroop12`) and password.

### Step 4: Push the Image to Docker Hub
```bash
docker push jayaswaroop12/carrental:latest
```

### Step 5: Verify on Docker Hub
Visit https://hub.docker.com/r/jayaswaroop12/carrental to see your image.

## Running the Container Locally (Optional Testing)

```bash
docker run -p 3000:3000 jayaswaroop12/carrental:latest
```

Then access the application at `http://localhost:3000`

## Dockerfile Details
- **Base Image**: Node.js 18 Alpine (lightweight)
- **Multi-stage build**: Reduces final image size
- **Serves on**: Port 3000
- **Build process**: 
  1. Installs dependencies
  2. Builds the Vite application
  3. Uses `serve` to serve the static files

## Troubleshooting

### Docker Desktop Not Running
- Start Docker Desktop from the Start menu
- Wait for it to initialize (check the system tray icon)

### Authentication Failed
- Ensure you're logged in: `docker login`
- Check your Docker Hub credentials

### Image Size Too Large
If the image is too large, consider:
- Using `.dockerignore` to exclude unnecessary files
- Implementing additional optimization in the Dockerfile

## Additional Tags (Optional)

You can also tag with version numbers:
```bash
docker build -t jayaswaroop12/carrental:v1.0.0 .
docker push jayaswaroop12/carrental:v1.0.0
```
