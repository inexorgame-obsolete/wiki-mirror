## Textures

Please use [webp](https://developers.google.com/speed/webp/) to store images for Inexor: It supports transparency (like png), animation (like gif) and has a better compression algorithm than jpeg.
We use [SDL_Image](https://www.libsdl.org/projects/SDL_image/) to decode images. Check their website for a full list of supported formats.

## Music / Sounds

Currently [ Ogg Vorbis ]( http://www.vorbis.com ) should be used to encode audio for inexor until [ SDL_Mixer ]( https://www.libsdl.org/projects/SDL_mixer/ ) supports [ Opus ]( http://www.opus-codec.org/ ). Unlike mp3 it's a royalty free file format and it provides a better compression than mp3.
Check out the SDL_Mixer website for a full list of supported sound formats.

## Models
Inexor can load the following file formats

* iqm (recommended)
* obj (recommended)
* md5
* md3
* md2
* smd

for skeletal and vertex animated characters, weapons, items, and world objects. Supports animation blending, procedural pitch animation, and ragdoll physics for skeletally-animated characters.
