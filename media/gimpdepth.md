# GIMP project bit depth: which to choose (8bit vs 16bit vs 32bit)

When creating a project on GIMP (and also most other image software), you can choose its bit depth between 8bit, 16bit and 32bit. It might not seem like it at first hand, but this choice matters a lot.

## What is bit depth?

The bit depth is the number of bits that represent a raw pixel or each colour channel of a pixel. Bit depth can be measured in bits per pixel or bits per channel. An 8bit/pixel image has 2^8 possible colours, which is a total of 256 colours. However, an 8bit/channel image has 256 possible values per each channel. If the 8bit per channel image has 3 channels (red, green and blue) then it's a 24bit/pixel image. If this same image also has a fourth channel for transparency (alpha), then it's a 32bit/pixel image.

## GIMP bit depth

A GIMP project's bit depth is measured in bits/channel. By default 8bit is usually selected, though you can change it at any time. Non-destructive filters and editing will have their bit depth changed and so will all layers, but anything that is destructive that was made in 8bit won't suddenly gain quality (for example brush painting).

## What does it matter for?

An image's bit depth defines the amount of colours it can have. An 8bit/channel image has 256 values for each channel, which results in nearly 17 million different possible colours. Sounds like a lot and it definitely is for a final image, but for production it's not enough because all kinds of edits and modifications can produce quantization errors.

An 8bit/channel GIMP project is very likely to result in [colour banding](https://en.wikipedia.org/wiki/Colour_banding), which is a visual defect where the [steps of a gradient or colour transition are very noticeable](https://en.wikipedia.org/wiki/Colour_banding#/media/File:Colour_banding_example01.png). 8bit is also not enough for colour grading and general filtering that is more intense and pushes the image to its limits.

The final exported image is rendered after everything is applied, and so 8bit is not an interference anymore as long as your project uses a high bit depth.

## Which bit depth to use?

Higher bit depths result in more colours which ends up with smoother gradients and more flexible/powerful and accurate editing and colour manipulation, but this has a resource toll. Project files become bigger, memory usage is higher and CPU usage is also higher.

If you can afford it, choose 16bit. This bit depth produces very decent results and for most cases will be indistinguishable from 32bit. Only choose 32bit if really needed. Avoid 8bit unless you have strict constraints on disk usage or performance.


## Is it worth it if the exported image is 8bit?

Yes. Your editing and quality advantages of 16bit and 32bit are not entirely lost if you export your image in 8bit. A lot of colour banding, ugly gradients and harsh colour transitions come from quantization errors when you are manipulating or creating an image, that's why it's important that the project itself is not 8bit. But when exporting a final image into 8bit, these quantization errors do not apply anymore as you are just rendering the final result. Yes, you lose colours (that you can't see anyways), but the final image looks very good and has smooth gradients.

In the end, a 16 or 32bit project exported into an 8bit image will have better and smoother gradients and colours than an 8bit project exported into an 8bit image.
