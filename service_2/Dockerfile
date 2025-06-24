FROM python:3.13-slim

# Install curl & uv
RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*
RUN pip install uv

# Set working directory
WORKDIR /app

# Copy all source code except .venv
COPY . .

# Install dependencies system-wide using uv (no .venv used)
RUN uv pip install --no-cache --system .

# Expose port
EXPOSE 8002

# Healthcheck
HEALTHCHECK --interval=30s --timeout=10s --retries=3 \
  CMD curl -f http://localhost:8002/ping || exit 1

# Run the app
CMD ["uv", "run", "app.py", "--port", "8002"]
