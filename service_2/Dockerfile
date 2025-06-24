FROM python:3.10-slim-bookworm

WORKDIR /app

RUN apt-get update && apt-get upgrade -y && \
    apt-get install --no-install-recommends -y curl git gcc libffi-dev && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Install uv and move it to global path
RUN curl -Ls https://astral.sh/uv/install.sh | bash && \
    cp /root/.local/bin/uv /usr/local/bin/uv

COPY . .

RUN uv pip install --system .

EXPOSE 8002

CMD ["uv", "run", "app.py"]
