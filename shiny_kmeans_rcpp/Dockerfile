# syntax = docker/dockerfile:1.3-labs

ARG R_VERSION
ARG SHINY_VERSION
FROM robertdj/shiny:${R_VERSION}-${SHINY_VERSION}

RUN <<EOF
apt-get update
apt-get install -y --no-install-recommends \
    libblas-dev \
    libarmadillo-dev \
    libarmadillo-dev \
    libarpack++2-dev \
    libgmp3-dev \
    libfftw3-dev \
    libtiff5-dev

rm -rf /tmp/*
rm -rf /var/lib/apt/lists/*
EOF

USER shiny

COPY --chown=shiny:shiny . /home/shiny/project/

RUN ln -s /home/shiny/project /srv/shiny-server/project

WORKDIR /home/shiny/project

