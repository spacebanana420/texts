# Codec vs. Video Format: Why H.264 Is Not a Codec

Have you ever heard someone call H.264 a "codec"? It happens very often, but it's not correct. People usually refer to H.264, H.265, VP9, etc as "codecs", and sometimes they are partially right, but that's not the case at all with H.264 and H.265.

## What is a codec?

A codec is a software program or library that can encode and decode data according to a certain format. Most of the times, the software either only encodes or decodes, so the term is not very accurate nowadays, but it still applies.

## What is H.264?

Definitely not a codec. H.264 and H.265 are video encoding formats. The format is the specification itself, now what's left is to have software implementation that can read and write into this format, that would be the codec.

Video formats are like file formats, they represent the specification for how data should be structured and written. Even after creating and designing the format, you still need something that creates it or reads it.

## What would be the codec then?

There are multiple encoding and decoding libraries/programs for the H.264 format. OpenH264 is a codec that can read and write video of this format. x264 is the most popular encoder for H.264, and while it only encodes and does not decode, the term "codec" is still appropriate. NVENC is the Nvidia hardware-based encoder for H.264 and H.265, and NVDEC is the decoding counterpart.

## Where did this confusion come from?

Many times, the creator of the format also creates the software implementation, this is the case with VP9 for example. VP9 is a video encoding format, but the codec is also called vp9. Even in the official webpage [VP9 is called a codec](https://www.webmproject.org/vp9/) because it's correct, the name is used for both the format and the codec.

This confusion is very common in image formats too, where the file format is also the compression format and the codec shares the same name. Other formats such as DNxHR also share the same name for the codec software.

## Video file format is not the video encoding format

Video files are more complicated than image or audio. A video file can contain video channels, audio channels and sometimes subtitle channels, and so the video's file format is not the same as the format of the video and audio streams themselves.

You can have 2 video files, one is MP4 and the other is MOV, and they have 100% identical video data, bit by bit. Both can use the H.264 format for video, and so you can encode in said format for both. What changes is how the file itself holds together the different media (video, audio, subtitles in case of MKV) and what features it supports (for example protection against corrupted data in MKV).
