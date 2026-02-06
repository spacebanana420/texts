# Pipewire: fixing audio crackling/popping and latency

Some people have issues with audio crackling or latency on Linux and that motivated me to write this guide as I’ve been doing some latency tests and came to very clear conclusions recently.

Pipewire docs: https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Config-PipeWire

Pipewire-pulse docs: https://docs.pipewire.org/page_module_protocol_pulse.html

Arch wiki: https://wiki.archlinux.org/title/PipeWire

Pipewire and Pulseaudio have countless settings, some of which directly affect your audio output latency as well as other issues such as audio crackling and CPU usage. This guide covers Pipewire specifically since the tendency is for more people to use it than Pulseaudio over time. This guide also covers pipewire-pulse a bit.

## Audio latency formula and settings

In `/etc/pipewire/pipewire.conf` lies the primary configuration file for Pipewire, inside it you have multiple settings. Look for the ones inside `context.properties`, specifically the settings `default.clock.rate`, `default.clock.quantum`, `default.clock.min-quantum` and `default.clock.max-quantum`.

Your Pipewire system’s latency is defined by the quantum size and the sample rate. The quantum size serves as a buffer while the sample rate serves as a temporal resolution.

Sound latency (in seconds) can be calculated with this formula:

`quantum_size / sample_rate`

To measure it in milliseconds, multiply the result by 1000:

`quantum_size / sample_rate * 1000`

Note that your real sound latency is a bit higher than the calculated value because of extra software overhead.

## Min, default and max quantum

The quantum size does not vary between min, default and max over time, instead each application chooses one of the 3 latency settings provided. Web browsers seem to use the maximum quantum size, while WINE seems to use the minimum quantum size.

## Setting audio latency and fixing audio crackling

Based on the formula written above, your audio latency is defined by both the quantum size and the sample rate. Most of us use 48KHz or 44.1KHz sample rates and have no real usecase for higher sample rates than that, and so I will assume that you are using 48KHz.

Adjusting your audio latency is as simple as changing the quantum size. Lower values result in lower audio latency but also higher CPU usage and eventually audio crackling if the system cannot keep up. Audio crackling is very common if you are running an application that uses the lowest quantum size while also using a lot of CPU. It can also happen if you are multitasking orjust have slow and old hardware.

Setting a decently low latency that does not result in audio crackling requires that you do some tests, but I have some values I recommend. My general recommendation for audio latency is for it to be equal or lower to 60Hz, which is 16ms. Latency below 20ms is likely to be imperceptible, but just to play safe a latency below 16ms is very decent.

The default min, default and max quantum sizes are exaggerated, as the minimum value is way too low, the default value is a bit too high and the maximum value is also too high.

This is the configuration I currently use:

```
default.clock.rate          = 48000
default.clock.allowed-rates = [ 48000 ]
default.clock.quantum       = 800
default.clock.min-quantum   = 512
default.clock.max-quantum   = 1024
```

I don’t have a big usecase for really low latency, so I use values below 20ms as reference. I use 512 quantum size for the minimum latency, and 800 for its default latency.

The maximum quantum value is usually used by applications that don’t require audio latency to be used properly, such as web browsers. Because of this, you can choose whatever high quantum size you want.

## Change pipewire-pulse too!

Quantum size settings are also available in `/etc/pipewire/pipewire-pulse.conf`. Scroll down to pulse.properties and find the place where `pulse.min.req`, `pulse.default.req`  and `pulse.min.quantum` are, and change the values to your liking. In this case, you provide not only the quantum size but also the sample rate. For example if you want a quantum size of 256 for `pulse.min.quantum` at 48KHz, set the value to `256/48000`.
