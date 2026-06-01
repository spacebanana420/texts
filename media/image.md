# Comparing Different Image Formats (PNG, JPG, AVIF, TIFF, WEBP, GIF, BMP)

This text aims to differentiate the various popular image formats and their strengths and weaknesses. I will separate them between the type of compression they support (lossless/uncompressed and lossy).

I will cover the following formats:
* PNG
* GIF
* JPG
* TIFF
* BMP
* WEBP
* AVIF

## Lossless formats

Lossless compression is a compression format that does not result in loss of information or quality. It's not exempt from loss of data unrelated to compression, such as lowering sample rate or color subsampling.

Lossless compression is also present in video, audio and non-media formats such as archive formats like ZIP. This compression type is essential for data and quality preservation.

Lossless compression is supported by:
* PNG
* GIF
* TIFF
* WEBP
* AVIF

## Uncompressed formats

Uncompressed image has absolutely no compression, storing raw pixel data. This results in significantly larger file sizes but the speed of reading and writing the images is much higher.

Uncompressed encoding is supported by:

* BMP
* TIFF

## Lossy formats

Lossy compression results in loss of data and quality, to achieve much smaller file sizes.

Lossy compression is supported by:

* JPG
* WEBP
* AVIF


## Describing Image Formats

### PNG

PNG is a general-purpose lossless image format, useful for high quality images for both personal and professional use.

Its specifications are:
* RGB color format
* Up to 16bit/channel bit depth
* Support for transparency
* Relatively fast read/write
* Decent file size

Its versatility makes it the universal image format.

### GIF

GIF is an animated image format, used for many memes but rarely for serious use. Despite being lossless, it only supports up to 8bit/pixel (256 colors).

Its specifications are:
* RGB color format
* 256 colors, 8bit/pixel
* Support for transparency
* Support for dithering and a custom palette
* Transparency support
* Reasonable read/write speeds
* Decent file size

### TIFF

TIFF is an image format that supports multiple compression formats as well as uncompressed. It's used in many professional contexts.

Its specifications are:
* RGB format
* Up to 32bit/channel bit depth
* Support for transparecy
* Support for multiple compression formats or uncompressed
* Basic layer support
* Fast to very fast read/write speed
* Large to very large file size

### WEBP

WEBP is an image format that is increasingly common on the web. A format as hated as it is misunderstood.

Its specifications are:
* RGB or YUV color format
* YUV color subsampling support
* 8bit/channel bit depth only
* Lossless and lossy compression
* Small to very small file sizes
* Decent read/write speed

### JPG

The most common lossy image format, used for all kinds of casual image consumption.

Its specifications are:
* YUV color format
* YUV color subsampling support
* 8bit/channel bit depth only
* Lossy compression
* Small file sizes
* Fast read/write speed

### BMP

An uncompressed image format, rarely seen today.

Its specifications are:
* RGB format
* 8bit/pixel depth up to 8bit/channel depth (24bit/pixel)
* Uncompressed
* Very fast read/write speed


### AVIF

A very versatile and highly efficient image format, its popularity is increasing on the web.

Its specifications are:
* RGB and YUV color formats
* YUV color subsampling
* 8bit, 10bit and 12bit (per channel) depth
* Lossless and lossy compression
* Small to incredibly small file sizes
* Very slow read/write speed


## Ranking image formats

### Quality
PNG and TIFF win here for having both lossless support as well as high bit depths. AVIF and WEBP have lossless support and BMP is uncompressed, but these formats do not support high bit depths.

### Read/write speed
BMP and uncompressed TIFF win as the fastest, JPG and WEBP are also pretty fast, followed by lossless TIFF and PNG. AVIF is very slow to encode and decode due to its complex compression.

### Compression efficiency
AVIF has the most efficient lossless and lossy compression, at the cost of speed. WEBP is also very efficient, not as much, but also much faster.

### Widespread support
PNG, GIF and JPG win here, they are used everywhere.

### Transparency
PNG, GIF and TIFF have transparency support.


## Conclusion

### When to use PNG?
This should be your default choice of image format unless you need smaller file sizes, uncompressed data or 32bit/channel depth.

### When to use JPG?
When quality and data loss is not important (for example, when sharing an image on the internet) but WEBP and AVIF are not supported.

### When to use GIF?
Only when you need animation or you are handling 8bit/pixel images (256 colors).

### When to use BMP?
Not much reason to unless if something you are doing requires BMP.

### When to use WEBP?
Same reason as JPG but when WEBP is well supported. It has better compression efficiency than JPG, so it will give lower file sizes for the same quality.

### When to use TIFF?
When you need 32bit/channel depth or when you need a faster/lighter compression than PNG.

### When to use AVIF?
Whenever it's supported and encoding speed is not a problem, you can use it instead of PNG for 8bpc to 12bpc images without transparency in lossless mode, or use it in lossy mode to achieve significantly better compression efficiency than JPG or WEBP.
