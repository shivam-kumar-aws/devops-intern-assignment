FROM python:3.11-slim

WORKDIR /app

# Install uv and Flask via requirements
RUN pip install --no-cache-dir uv

# Copy source files
COPY app.py requirements.txt README.md ./

# Install Flask using uv
RUN uv pip install --requirement requirements.txt --system

EXPOSE 8002

CMD ["uv", "run", "app.py"]
