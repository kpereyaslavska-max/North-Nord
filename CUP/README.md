# Jupyter Notebook Docker Setup

This Docker Compose setup provides a Jupyter Notebook environment with pre-installed data science libraries.

## Included Libraries

- **pandas** - Data manipulation and analysis
- **numpy** - Numerical computing
- **matplotlib** - Plotting and visualization
- **scikit-learn** - Machine learning
- **scipy** - Scientific computing
- **plotly** - Interactive plotting

## Getting Started

### Prerequisites

- Docker
- Docker Compose

### Installation & Usage

1. Build and start the container:
   ```bash
   docker-compose up -d
   ```

2. Access Jupyter Notebook in your browser:
   ```
   http://localhost:8888
   ```
   
   Note: Authentication is disabled by default for local development.

3. Your notebooks will be saved in the `./notebooks` directory on your host machine.

### Useful Commands

- **Start the container:**
  ```bash
  docker-compose up -d
  ```

- **Stop the container:**
  ```bash
  docker-compose down
  ```

- **View logs:**
  ```bash
  docker-compose logs -f
  ```

- **Rebuild the container (after changing requirements.txt):**
  ```bash
  docker-compose up -d --build
  ```

- **Access container shell:**
  ```bash
  docker exec -it jupyter-notebook bash
  ```

## Directory Structure

```
.
├── docker-compose.yml    # Docker Compose configuration
├── Dockerfile           # Docker image definition
├── requirements.txt     # Python dependencies
├── notebooks/          # Your Jupyter notebooks (created automatically)
└── README.md           # This file
```

## Customization

### Adding More Python Packages

Edit `requirements.txt` and add your desired packages, then rebuild:

```bash
docker-compose up -d --build
```

### Enabling Authentication

To enable token-based authentication, modify the `docker-compose.yml` file and remove the `--NotebookApp.token=''` and `--NotebookApp.password=''` flags from the command.

### Changing the Port

To use a different port, modify the ports section in `docker-compose.yml`:

```yaml
ports:
  - "YOUR_PORT:8888"
```

## Troubleshooting

- If port 8888 is already in use, change the host port in `docker-compose.yml`
- If you encounter permission issues with the notebooks directory, check the ownership and permissions

