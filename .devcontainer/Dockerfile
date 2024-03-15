# [Choice] Ubuntu version (use jammy on local arm64/Apple Silicon): jammy, focal
ARG VARIANT="jammy"
FROM buildpack-deps:${VARIANT}-curl

LABEL dev.containers.features="common"

# install base packages
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends build-essential binutils-arm-none-eabi git libpng-dev
# install devKitPro
RUN wget https://apt.devkitpro.org/install-devkitpro-pacman \
    && chmod +x chmod +x ./install-devkitpro-pacman \
    && ./install-devkitpro-pacman
# install gba-dev
RUN dkp-pacman -Sy \
    && dkp-pacman -S gba-dev \
    && source /etc/profile.d/devkit-env.sh
