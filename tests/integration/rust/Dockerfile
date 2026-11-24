FROM rust:slim@sha256:3b199fd6db7d709274df56565b8f4003f9e30d7bfcff9d53148c86053b7855e2
RUN apt-get update \
    && apt-get install -y --no-install-recommends pkg-config libssl-dev \
    && rm -rf /var/lib/apt/lists/*
WORKDIR /app
COPY Cargo.toml .
# Pre-compile dependencies with a dummy main so real builds are fast
RUN mkdir src && echo 'fn main() {}' > src/main.rs && cargo build --release && rm src/main.rs
ENTRYPOINT ["sh", "-c", "if [ -z \"$INSTALL_DEPS\" ]; then echo 'INSTALL_DEPS is required for Rust integration tests.' >&2; exit 1; fi && cp /code/main.rs src/main.rs && eval \"$INSTALL_DEPS\" && cargo build --release && ./target/release/stac-search"]
