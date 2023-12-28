# syntax=docker/dockerfile:1
# see: https://linuxhint.com/how-to-use-apt-install-correctly-in-your-dockerfile/
FROM mcr.microsoft.com/devcontainers/python:1-3.12-bookworm
RUN pip install --upgrade pip
# Install Poetry
# see: https://towardsdatascience.com/a-poetic-apology-71a41db4ecce
RUN python -m pip install --user pipx && \
    python -m pipx ensurepath && \
    pipx install poetry
RUN apt-get update && apt-get install -y --no-install-recommends \
    hexyl \
    pandoc \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
# Install a few goodies if you want to use them.
# Chezmoi
RUN sh -c "$(curl -fsLS get.chezmoi.io)"
# NixOX package manager
RUN su vscode --command "sh <(curl -L https://nixos.org/nix/install) --no-daemon"
