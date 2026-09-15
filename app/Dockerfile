FROM python:3.12-slim-bookworm

WORKDIR /app

# 1. Update OS packages to fix Debian vulnerabilities and clean up cache
RUN apt-get update && apt-get upgrade -y && \
    rm -rf /var/lib/apt/lists/*

COPY requirements.txt .

# 2. Install uv and use it to install requirements system-wide
RUN pip install --no-cache-dir uv && \
    uv pip install --system --no-cache -r requirements.txt

COPY . .

EXPOSE 8000

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]