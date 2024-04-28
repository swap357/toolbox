This Docker image provides a lightweight Alpine Linux environment with Python built from source, including debug symbols. The image is designed to aid in debugging Python applications, profiling, and performance optimization.
## Key Features

- Based on Alpine Linux 3.19.1 for a minimal and secure base image
- Python built from the official CPython repository with debug symbols enabled
- Includes necessary build and runtime dependencies
- Optimized multi-stage build to keep the final image clean and small
- Preconfigured environment variables for easy integration

## Intended Use
This image is ideal for developers and teams working on Python projects that require in-depth debugging, profiling, and performance optimization. By providing a pre-built environment with Python debug symbols, this image saves time and effort in setting up a debugging environment from scratch.
Use this image as a base for your Python application Docker images, or as a standalone container for debugging and profiling purposes. Simply pull the image and run your Python application or debugging tools inside the container.

## Getting Started
To get started, pull the image from Docker Hub:
```
docker pull swap357/python-debug
```

Then, run your Python application or debugging tools inside the container:
```
docker run -it --rm swap357/python-debug script.py
```