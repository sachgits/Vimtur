# Media viewer and organiser

![Preview Image](screenshots/view.png)

## Features
* Web-based interface
* Video, gif and image support
* Tagging media
* Various forms of searching (weighted keyword, tag selection, expression)
* Metadata support for Artist/Album/Title/[People/Actors]
* Auto-scraped metadata from files where possible
* Internal image gallery for faster browser
* Thumbnail generation for all media
* Auto-transcode videos for web-browser compatibility
* Electron support
* Import and export database to JSON format
* Rating system

## Notes
* Requires ffmpeg for transcoding and thumbnails (included). Requires graphicsmagick for extracting EXIF data.
* Caching data takes a lot of space. All videos are re-transcoded to be h264 and HLS compatible.
* Because of pre-caching it's possible to quickly skip through videos and loading times are minimal.
* All videos are transcoded to a high-quality, if the source video is h264 it's just copied. Often this means h264 source videos are transcoded quickly but it also means a reasonably fast network is required.
* Tested on Ubuntu 16.04 & 18.04 64-bit and Windows 10 64-bit.

## Setup
On Ubuntu/Debian run:
sudo apt-get install graphicsmagick

For Windows install graphicsmagick.

### As a server
`npm install && npm run server`

### As an Electron app
`npm install && npm run postinstall && npm run electron`

Or to create binaries run:
`npm install && npm run dist`

## Running
Specifying a path as the last argument when doing any launch will set the config to be used by the instance.
Such as: `npm run start /data/Pictures/config.json`.
Doing this allows multiple libraries to be acessed, if it's not specified a default config.json is created in the application directory.

## Docker
The server can be run as a Docker instance. It accepts the following environment variables:
* (required) DATA_DIR - The path to the media library.
* (required) CACHE_DIR - The directory to cache thumbnails, videos, and store the config and database. Cannot be inside the DATA_DIR.
* (optional) USERNAME - A username to login with. PASSWORD also required.
* (optional) PASSWORD - A password to login with. USERNAME required too.
* (optional) PORT - A port for the Docker instance to expose. Default 3523.

## Example
```DATA_DIR=/home/user/Pictures CACHE_DIR=/home/user/cache docker-compose up```

## Screenshots
![Preview Image](screenshots/admin.png)
![Preview Image](screenshots/metadata.png)
![Preview Image](screenshots/search.png)
