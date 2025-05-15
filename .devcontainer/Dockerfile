FROM mcr.microsoft.com/devcontainers/javascript-node

USER root

# --- INSTALL Node.js 20, npm, Angular CLI ---
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get install -y nodejs \
    && npm install -g npm \
    && npm install -g @angular/cli

# Optional: clean up apt caches (good practice)
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
