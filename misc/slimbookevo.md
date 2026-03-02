# Slimbook Evo 8845HS Review

As a hardcore Linux user and a lover for durable and repairable hardware I've always had some interest in getting my hands on one of those "Linux-friendly" laptops that some smaller companies make. I use my laptop on a daily basis and I need portability all the time, and by late-2024 to early-2025 my current laptop was having its own issues. These issues are not uncommon, they arise in laptops that are not meant to last or meant to be repaired (or you can repair them but for ridiculous prices). It was time I bought a new laptop, and in June 2025 I got myself the Slimbook Evo 8845HS. A new model with a more modern CPU was released already and so this review might be a bit outdated, especially in the audio issue part I will write below:

### Slimbook Evo 8845HS overview

The Slimbook Evo 8845HS laptop is a powerful general-purpose laptop great for all kinds of needs. It comes with the AMD Ryzen 8845HS CPU and the AMD 780M integrated graphics. It has a phenomenal screen at 2560x1600@120Hz with a claimed color gamut of 100% sRGB. This laptop is built for all kinds of tasks, from CPU-intensive workloads to gaming to artistic creation.

### Why Slimbook?

I needed the durability and repairability of a business-grade laptop (such as Thinkpads), but I did not want to buy a refurbished one that is years behind in CPU and GPU then also have a dull screen. Slimbook laptops are the best of both worlds: it's repairable and durable while also having modern hardware.

### Exterior Build Quality

The Slimbook Evo has a very decent build quality. It's thin and lightweight but feels sturdy and after nearly a year of use I don't notice degradation or damage.

### Ports

The Slimbook Evo comes with the typical amount of ports you would see in a modern laptop, having 3 USB ports, an audio jack port, but also ethernet port, an SD card port and 2 USB-C ports, both of which can charge the laptop and output graphics to a monitor.

### Charging

The Slimbook Evo has 2 USB-C ports which can be used for devices, monitors, docking stations and, of course, charging. The Evo can charge at up to 100W. The laptop comes with its own 100W charger, but if you happen to need a second one like I did, it's best to buy the older charger for Evo available on their site, since it's cheaper, smaller but can still charge at 100W.

### Audio Jack integrity

It's very typical for a laptop's audio jack to degrade over time as you use it. After 7-8 months of use, my jack port is not damaged and does not have newly-introduced noise or signal issues, but the grip is loose and so the cable can more easily be detached from it. It's not a big deal for now, I just hope it doesn't evolve from here.

### CPU and GPU

My model of Slimbook Evo uses the Ryzen 7 8845HS CPU, with the AMD 780M iGPU. At 8 cores 16 threads, 3.8GHz base speed and up to 5.14 turbo speed, this CPU is very powerful, but what shocked me the most was how efficient it was. At full load in alll threads at 3.8GHz, the CPU doesn't even reach 70 degrees celsius, it barely even approaches 66! I have never in my life seen a CPU so simultaneously fast and cool.

The integrated GPU is quite powerful for what it is. The AMD 780M iGPU is, in speed, comparable to a desktop GTX 1050 TI, making it very suitable for playing lots of games. You will of course struggle with the latest AAA games, especially if you use the native resolution of 2560x1600

### The Screen

I love the Evo's screen. 2560x1600 is a very high resolution which makes text and image graphics very clean and crisp, though for gaming you won't care much. If you struggle with gaming performance, consider dropping resolution to 1920x1200.

The screen refresh rate of 120Hz is beautiful to both use it on general daily use as well as gaming. Mouse input is more responsive and of course everything is smoother, playing games at this refresh rate was a bit sickening to me at first but I got used to it very fast and I like it.

The screen's contrast is decent, though close to average, but the colors are really good. The Evo's screen has a reported color gamut of 100% sRGB, making colors vivid, intense and more accurate. I felt that the screen had a slightly yellowish tint but I'm unsure if that was just me being used to screens with other tints, eventually the brian adapts due to how minor the difference is and you end up seeing pure white.

### Keyboard

The keyboard feels sturdy and there is no sight of a key or its shell to be close to being damaged, unlike on mainstream consumer-grade laptops. Sometimes, the plastic frame below the keys can interfere with key presses it seems, but it's a very minor annoyance.

With certain key press combinations, very minor keyboard ghosting can happen. You will not notice this at all with gameplay that uses WASD/QUERTY for movement, which is great. I do notice a bit of ghosting while playing Touhou, but it only happens if I use 2 arrow keys while holding Z and shift at the same time, then I want to press X to bomb and it won't work. Very minor ghosting, not a problem to me at all.

Input lag is very low on the keyboard, no problems playing games that require very low latency (such as Touhou or even rhythm games).

### Power consumption

Slimbook Evo's power consumption sits at around 6W to 9W in idle, depending on brightness, OS, software, etc. I tested it on Artix Linux with Xfce 4.20 and very few background services running. When you start using the hardware intensely, power consumption doesn't scale too much.

### UEFI

Slimbook Evo's UEFI is flexible and powerful. It allows you to set many options, some of which are the charging speed limit (100W or 85W), battery charge limit (60%, 80% or 100%) and pre-allocation of RAM into VRAM for the graphics chip. Updating UEFI is more manual and requires you to run commans in a built-in shell, which might intimidate people unused to command-line or people generally afraid of updating BIOS, but Slimbook has a guide showing the exact steps.

### Linux Support

Almost everything works perfectly out of the box regardless of OS, except that you need to [configure a kernel parameter to fix a very annoying graphics bug](../guides/amd780m.md), and ethernet firmware is not included in the Linux kernel, must be installed separately. SlimbookOS has a package for this ethernet (probaby pre-installed too) and I belive the GPU fix is pre-applied, though if you decide to use your own OS of choice you will have to tinker with this a bit.

### Repairability

Slimbook offers all kinds of replacement parts for their laptops, though in their website not much shows up for the Evo. However, Slimbook support told me that you can request a part for replacement through e-mail if it's not available on the website. Replacement parts are mostly affordable and you shouldn't worry much about having a damaged laptop forever, however I did notice that batteries are unusually expensive.

### Battery

This laptop comes with a 99Wh battery, which is a very decent amount of charge. I never charge it to 100% or discharge to 0% for health reasons and because most of the times my laptop is plugged, and so every here and there the battery charge report eventually becomes inaccurate and the battery re-calibrates itself.

After nearly a year of usage, the battery still reports 100% health and, the most weird part, 0 charge cycles. I don't trust the charge cycles report because by now it should have increased.

### Speakers, Microphone and Webcam

The speakers are surprisingly good and I really appreciate that. Sound is crisp and decently accurate for laptop speakers. Low frequencies are lacking as you would expect, but overall sometimes I prefer to simply use the laptop's speakers over my own Sennheiser headphones.

The microphone is a bit muffled but not hard for people to understand what you are saying. It's usable, not the best.

Webcam quality isn't extraordinary, it does its job, good for voice chat but not for livestreaming.

### Intense lights

The power button light and the webcam light can be a bit intense. Sadly there's no option in UEFI to control this. I genuinely considered covering the power button's light with tape at some point.

### An audio quirk, the biggest issue of the Evo

For headphone jack connections, there is a very cryptic issue that I have never seen before on hardware. This does not happen if you use the speakers, bluetooth headphones or USB headphones, but does happen with jack headphones. I'm unsure if it only happens with 3-ring headphones (no built-in mic) or if it happens on all jack connections.

When you use jack headphones, every time you stop transmitting audio from the system to your headphones, there is a relatively low probability that a high-pitch ringing (somewhere between 8KHz and 15KHz probably) is heard on one of your ears continuously until you play audio again on your system. This is very irritating when it happens, but it doesn't happen too often for me to consider not using the jack audio at all. How often this happens seems to vary, but I haven't find any pattern, culprit or solution to this problem after months of extremely intensive troubleshooting and contact with Slimbook support. If this is a driver/firmware issue, it might be fixed eventually with a Linux firmware update or UEFI update. If it's an issue in the audio chip itself then it will probably never change. I don't know if the latest Evo has this problem.

## Conclusion

The Slimbook Evo is my dream laptop, with the exact specs I want, kind of a master-of-all-trades. It's a near-perfect all-rounder laptop, it's just a shame that the audio jack quirk exists. If you strongly depend/desire using headphones with jack connection, the quirk I said above might be irritating for you.
