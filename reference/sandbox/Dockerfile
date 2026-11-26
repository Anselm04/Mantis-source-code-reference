# Sandbox image for the reproducer and patcher nodes.
# Built once by an operator — never by an agent.
FROM python:3.15.1-slim@sha256:533b0b2f9b5d46fd097091cf826f27902f1d6c3bca714b6dc74551356aa97a51

# The sandbox has no network (Network.none()), so nothing can be installed at
# run time. Add your target's dependencies here.
RUN apt-get update \
 && apt-get install -y --no-install-recommends patch \
 && rm -rf /var/lib/apt/lists/*
COPY requirements.txt .
RUN pip install --require-hashes --no-cache-dir -r requirements.txt

WORKDIR /workspace
