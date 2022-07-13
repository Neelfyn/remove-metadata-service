# Remove Metadata
[Remove Metadata](https://github.com/Neelfyn/remove-metadata-service) is a Quick Action for macOS. It adds a "service" context menu item, as well as an icon in the preview bar in the Finder, which both let you conveniently strip metadata (such as camera model and GPS location) from images, PDFs, and some video files.

## Installation

[Download the latest release](https://github.com/Neelfyn/remove-metadata-service/releases), unzip it, and double-click `Remove Metadata.workflow`. Then, click *Install*. That's it!

## Usage

In the Finder, right-click a supported file, such as a JPG image, and select "Remove Metadata". Alternatively, if you've enabled *Show Preview* in the Finder's *View* menu, a "Remove Metadata" icon should appear underneath the preview, or in the *More* menu.

A cog icon will briefly appear in your menu bar. When the cog icon has disappeared, your selected file has been cleaned.

Please note that the original file is overwritten. If you require a copy of your file with the metadata, make sure to duplicate it before clicking "Remove Metadata".

![Remove Metadata in the Finder context menu](/Screenshots/context_menu.png?raw=true)

![Remove Metadata in the Finder preview pane](/Screenshots/preview_pane.png?raw=true)

It is also possible to select multiple supported files at once.

## FAQ

### Why would I want to use this?

Whenever you take a picture with your smartphone or camera, a whole bunch of information is saved along with the picture itself. This information often includes, but is not limited to:

* Name of the manufacturer of the phone/camera
* Model of the phone/camera
* Date and time
* GPS coordinates
* Details about the lens
* Camera modes and settings (e.g. whether the flash was used)
* Sometimes even your full name!

This is very useful for sorting and searching through your pictures, however, perhaps not all of this information is something you would like to share when publishing a picture online or sharing it with someone. Remove Metadata deletes as much of this information as possible, while your picture itself will still look the same.

Many other file types (e.g. PDFs, videos, music, some types of documents) also include metadata when they're saved, with varying types of information. Remove Metadata can also help you clean up some of these other file formats. You can find the list below.

### How does it work?

Remove Metadata is a simple Automator wrapper for the excellent [ExifTool](https://exiftool.org/) by Phil Harvey, which is bundled within the `.workflow` file itself: no need to install any dependencies. All it currently does is run `exiftool -q -all= -TagsFromFile @ -ColorSpaceTags -overwrite_original_in_place` on items you've selected in the Finder — so that you can skip a step and not have to switch over to a terminal or some other app to anonymize your photos before sharing them.

### How do I know that it worked?

You can see the metadata of images and PDFs in the Preview app, under *Tools > Show Inspector > More info (i icon)*. For audio and video files, the QuickTime app has a similar *Show Movie Inspector* entry in the *Window* menu.

It is also possible to see some of the metadata by right-clicking on a file in the Finder, and selecting *Get Info*, however it will not be as complete.

### What formats are supported?

Pictures:

* PNG
* JPG, JPEG
* JPEG 2000
* HEIC, HEIF
* TIFF
* Photoshop, Illustrator
* PostScript
* DNG
* Various camera RAW files 

Documents:

* PDF

Audio/video:

* QuickTime (mov)
* MPEG-4 (mp4)
* m4a, m4v
* 3gpp, 3gpp2

### How do I uninstall Remove Metadata?

Open System Preferences, then go to *Extensions > Finder*, right-click *Remove Metadata* and select *Move to Trash*.

Alternatively, delete the file at `~/Library/Services/Remove\ Metadata.workflow`.

## License

Just like the bundled ExifTool, this is free software. You can redistribute it and/or modify it under the same terms as [Perl itself](http://dev.perl.org/licenses/).
