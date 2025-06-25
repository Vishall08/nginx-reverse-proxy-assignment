# Use a minimal Python base image
FROM python:3.11-slim

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Set working directory
WORKDIR /app

# Install curl and uv
RUN apt-get update && \
    apt-get install -y curl && \
    curl -Ls https://astral.sh/uv/install.sh | sh && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Add uv to PATH
ENV PATH="/root/.local/bin:$PATH"

# Copy the application code
COPY . .

# Install Flask using uv
RUN uv pip install flask --system

# Expose the port the Flask app uses
EXPOSE 8002

# Run the app using uv
CMD ["uv", "run", "app.py"]
