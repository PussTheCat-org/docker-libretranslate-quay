FROM python:3.10-slim-bullseye
WORKDIR /libretranslate
RUN apt update -y && apt upgrade -y \
    && apt install -y --no-install-recommends libicu-dev pkg-config gcc g++ git \
    && apt autoclean -y \
    && apt autoremove -y \
    && rm -rf /var/lib/apt/lists/* \
    && pip install --upgrade pip \
    && git clone --depth=1 https://github.com/LibreTranslate/LibreTranslate . \
    && pip install -e . \
    && python3 install_models.py \
    && pip install . \
    && pip cache purge
EXPOSE 5000
ENTRYPOINT [ "libretranslate", "--host", "0.0.0.0" ]
