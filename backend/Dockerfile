# 1. Base Image MUST be the first non-comment line
FROM python:3.11-slim

# 2. Modern libraries for MediaPipe/OpenCV (The fix from the previous step)
RUN apt-get update && apt-get install -y \
    libgl1 \
    libglx-mesa0 \
    libglib2.0-0 \
    && rm -rf /var/lib/apt/lists/*

# 3. Setup App directory
WORKDIR /app

# 4. Install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 5. Copy the rest of your backend code
COPY . .

# 6. Start the server
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8080"]