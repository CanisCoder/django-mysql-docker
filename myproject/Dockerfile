# Use Python slim image
FROM python:3.9-slim

# Prevent Python from writing .pyc files to disk
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libmariadb-dev-compat \
    libmariadb-dev \
    gcc \
    pkg-config \
    python3-dev \
    build-essential \
    && apt-get clean

# Set the working directory in the container to /code
WORKDIR /code

# Install Python dependencies from requirements.txt
COPY requirements.txt /code/
RUN pip install --no-cache-dir -r requirements.txt

# Copy the entire project folder to /code in the container
COPY myproject /code/

# Expose port 8000 for Django development server
EXPOSE 8000

# Set the entry point to run the Django development server
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
