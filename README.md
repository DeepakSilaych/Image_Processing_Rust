# Image Processing Service

A high-performance image processing service written in Rust, focusing on face detection, alignment, quality assessment, and feature extraction. This service is designed to work with NVIDIA Triton Inference Server for efficient model serving.

## Features

- Face Detection using RetinaFace
- Face Selection and Alignment
- Face Quality Assessment
- Facial Feature Extraction
- Anti-Spoofing Detection
- RESTful API endpoints
- OpenTelemetry integration for observability
- Docker support
- Comprehensive logging

## Project Structure

```
.
├── src/
│   ├── config/         # Configuration management
│   ├── error/          # Error handling
│   ├── handler/        # Request handlers
│   ├── logger/         # Logging setup
│   ├── middleware/     # HTTP middleware
│   ├── models/         # Data models
│   ├── pipeline/       # Image processing pipelines
│   ├── repository/     # Data persistence
│   ├── response/       # Response types
│   ├── routes/         # API routes
│   ├── service/        # Business logic
│   ├── state/          # Application state
│   ├── tracer/         # OpenTelemetry setup
│   └── utils/          # Utility functions
├── conf/               # Configuration files
├── triton_proto/       # Triton Inference Server protobuf definitions
├── Cargo.toml          # Rust dependencies
├── Dockerfile          # Container configuration
└── Makefile           # Build and deployment commands
```

## Prerequisites

- Rust 2021 edition or later
- Docker (optional, for containerized deployment)
- NVIDIA Triton Inference Server with the following models:
  - Face Detection (RetinaFace)
  - Face Quality Assessment
  - Face Feature Extraction
  - Anti-Spoofing Detection

## Setup

1. Clone the repository:

```bash
git clone <repository-url>
cd rs-image-processing-svc
```

2. Configure environment variables:

```bash
cp .env.example .env
# Edit .env with your configuration
```

3. Build the project:

```bash
cargo build --release
```

4. Run the service:

```bash
cargo run --release
```

## Docker Deployment

Build the Docker image:

```bash
docker build -t rs-image-processing-svc .
```

Run the container:

```bash
docker run -p 8080:8080 rs-image-processing-svc
```

## API Endpoints

The service exposes the following endpoints:

- `POST /api/v1/face/extract` - Extract facial features from an image
- `POST /api/v1/face/antispoof` - Check for face spoofing attempts
- Additional endpoints for health checks and monitoring

## Configuration

The service can be configured through environment variables or configuration files in the `conf/` directory. Key configuration options include:

- Server port and host
- Triton Inference Server connection details
- Logging levels
- OpenTelemetry settings

## Development

### Running Tests

```bash
cargo test
```

### Code Style

The project uses:

- `rustfmt` for code formatting
- `clippy` for linting

Run formatting:

```bash
cargo fmt
```

Run linting:

```bash
cargo clippy
```
