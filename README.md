# docker-libretranslate-quay

A [LibreTranslate](https://github.com/LibreTranslate/LibreTranslate) image, on Quay.

[Quay page](https://quay.io/repository/pussthecatorg/libretranslate) | [GitHub page](https://github.com/TheFrenchGhosty/docker-libretranslate-quay)

This image mostly exist for the [PussTheCat.org](https://pussthecat.org/) [instance](https://libretranslate.pussthecat.org/), but others are free to use it.

## Differences with the official image:

- The translation models are included so that the image can actually run when it's started (instead of requiring the user to jump into the container to run the script installing the models, and [breaking catastrophically](https://github.com/LibreTranslate/LibreTranslate/issues/185) when some models fail to download), this creates massive images, around 12GB compressed and 14.5GB uncompressed (instead of around 1GB compressed and around 2.5GB uncompressed for the official image) but it is a worthy tradeoff to have something that works instantly and reliably. Running LibreTranslate requires those models no matter what, so in the end, running the official image will requires the same amount of disk space, this image just does it in a better way.
- The `Dockerfile` cleaner and simplified
- The `docker-compose.yml` actually has persistence for the api keys and the suggestions storage

## Usage:

- Make a folder where you want the LibreTranslate data to be
- Download (or copy the content of) the `docker-compose.yml` and place in this folder
- Create empty files in this folder (so that docker doesn't make folder with their name): `touch api_keys.db suggestions.db`
- (Optional) Customize the environment variable with the settings you want to apply, following the official README: https://github.com/LibreTranslate/LibreTranslate#arguments
- `docker-compose up -d`
