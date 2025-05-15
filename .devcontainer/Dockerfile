ARG TARGET_JAVA_VERSION=21
ARG BASE_IMAGE_VERSION_CODENAME=bookworm
FROM mcr.microsoft.com/devcontainers/base:${BASE_IMAGE_VERSION_CODENAME}

USER root
ARG TARGET_JAVA_VERSION
ENV JAVA_HOME /usr/lib/jvm/msopenjdk-current
ENV PATH "${JAVA_HOME}/bin:${PATH}"
ENV LANG en_US.UTF-8

# --- INSTALL Microsoft OpenJDK ---
RUN arch="$(dpkg --print-architecture)" \
	&& case "$arch" in \
		"amd64") jdkUrl="https://aka.ms/download-jdk/microsoft-jdk-${TARGET_JAVA_VERSION}-linux-x64.tar.gz" ;; \
		"arm64") jdkUrl="https://aka.ms/download-jdk/microsoft-jdk-${TARGET_JAVA_VERSION}-linux-aarch64.tar.gz" ;; \
		*) echo >&2 "error: unsupported architecture: '$arch'"; exit 1 ;; \
	esac \
	&& wget --progress=dot:giga -O msopenjdk.tar.gz "${jdkUrl}" \
	&& wget --progress=dot:giga -O sha256sum.txt "${jdkUrl}.sha256sum.txt" \
	&& sha256=$(cut -d ' ' -f1 sha256sum.txt) \
	&& echo "${sha256} msopenjdk.tar.gz" | sha256sum --strict --check - \
	&& mkdir -p "$JAVA_HOME" \
	&& tar --extract --file msopenjdk.tar.gz --directory "$JAVA_HOME" --strip-components 1 --no-same-owner \
	&& rm -f msopenjdk.tar.gz* sha256sum.txt* \
	&& ln -s ${JAVA_HOME} /docker-java-home \
	&& ln -s ${JAVA_HOME} /usr/local/openjdk-${TARGET_JAVA_VERSION}

# --- INSTALL Node.js 20, npm, Angular CLI ---
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get install -y nodejs \
    && npm install -g npm \
    && npm install -g @angular/cli

# Optional: clean up apt caches (good practice)
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
