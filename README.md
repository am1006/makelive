# MakeLive

Convert an photo + video pair into a Live Photo.

This is a simple command line tool that will apply the necessary metadata to a photo + video pair so that when they are imported into the Apple Photos, they will be treated as a Live Photo.

## Usage

```bash
makelive photo.jpg video.mov
```

## Requirements

* macOS (Tested on 13.5.1; should work on 10.15+)
* Python 3.9+

## Installation

* `pip install flit`
* `flit install`

## API

```python
from makelive import make_live_photo

photo_path = "test.jpg"
video_path = "test.mov"
asset_id = make_live_photo(photo_path, video_path)
print(f"Wrote Asset ID: {asset_id} to {photo_path} and {video_path}")
```

## How it works

In order for Photos to treat a photo + video pair as a Live Photo, the video file must contain a Content Identifier metadata tag set to a UUID. The associated photo must contain a Content Identifier metadata tag set to the same UUID. Unfortunately, these tags cannot be written with the standard [exiftool](https://exiftool.org/) utility if they do not already exist in the file as the metadata is stored in Maker Notes which exiftool cannot create.

This tool uses the Core Graphics and AV Foundation frameworks to modify the metadata of the photo and video files.

## Caution

This tool has not yet been extensively tested. It is recommended that you make a backup of your photo and video files before using this tool as it will overwrite the files.

## Source Code

The source code is available [here](https://github.com/RhetTbull/makelive).

## License

MIT License, see [LICENSE](LICENSE) for details.

## Credits

The [Live-Photo-master](https://github.com/GUIYIVIEW/LivePhoto-master) project by [GUIYIVIEW](https://github.com/GUIYIVIEW) was helpful for understanding how to set the asset ID in the QuickTime file. Copyright (c) 2017 GUIYIVIEW and [published under the MIT License](https://github.com/GUIYIVIEW/LivePhoto-master/blob/master/LICENSE).
