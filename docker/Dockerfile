FROM python:3.13-slim-bookworm

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        git \
        libgl1 \
        libgomp1 \
        libsm6 \
        libxi6 \
        libxkbcommon-x11-0 \
        libxrender1 \
        libxxf86vm1 \
        mesa-utils \
    && rm -rf /var/lib/apt/lists/*

COPY src/requirements.txt /tmp/requirements.txt
RUN python -m pip install --no-cache-dir -r /tmp/requirements.txt

COPY src /opt/ud-caves/src
WORKDIR /opt/ud-caves/src

ENTRYPOINT ["python"]
