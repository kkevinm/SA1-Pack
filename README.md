﻿```
   _____             __     _____           _
  / ____|  /\       /_ |   |  __ \         | |
 | (___   /  \ ______| |   | |__) |_ _  ___| | __
  \___ \ / /\ \______| |   |  ___/ _` |/ __| |/ /
  ____) / ____ \     | |   | |  | (_| | (__|   <
 |_____/_/    \_\    |_|   |_|   \__,_|\___|_|\_\
   by Vitor Vilela                 Version 1.27
```

The SA-1 Pack is a package of patches for activating and optimizing the SA-1
system for the SMW ROM, with emphasis on eliminating slowdown, game limitations
and accelerating the engine to the maximum possible.

What is it?
===========

SA-1 is a co-processor used on some special SNES games, made to work together
with the Super NES CPU and enhance its processing speed, graphics and memory.

With its base 10.74 MHz clock, the SA-1 CPU is four times faster than the
normal SNES CPU processing. The SA-1 CPU and SNES CPU also runs
simultaneously, which can result in five times faster processing over game with
a standard cart setup. With that much power, the Super Accelerator System (SAS)
can be used to handle the SMW engine much faster than the normal, allowing more
sprites to be processed at once, more in-game effects, faster level loading and
much more.

SA-1 Pack not just activates the co-processor, but also modifies a good part of
the game engine to use and explore the chip features, which gives an extreme
boost to the overall performance of the game.

## Game Features
* Makes the game run up to four times faster.
* Increase the maximum amount of sprites at once on screen to 22.
* Increase the maximum amount of sprites on a single sub-level to 255.
* Reduces loading time of all levels and maps.
* Increase the maximum ROM size to 8 MB.
* Offers enhanced bitmap and arithmetic capabilities for better graphics
performance.

## System Features
* 16-bit 65c816 processor clocked at 10.74 MHz.
* 2 kB fast internal work memory (I-RAM), clocked at 10.74 MHz.
* Multi-processor processing, with parallel operating mode and memory sharing
control.
* Large capacity memory, with a total capability of 8 MB of ROM clocked at
10.74 MHz and 256 kB of BW-RAM, clocked at 5.37 MHz.
* High speed arithmetic hardware of multiplication, division and cumulative
sum.
* Bitmap and Character Conversion functions for fast graphics manipulation.
* Custom DMA circuit for fast transfers between ROM, I-RAM and BW-RAM.
* Variable-Length Bit data processing for enhanced algorithms such as graphics
and data compression.
* Super MMC memory mapping capabilities for BW-RAM and bank switching for
multiple ROM image access and mirroring.

Compatibility
=============

SA-1 Pack is the most complex patch ever made to Super Mario World. It modifies
pretty much the entire game, because the patch moves most of the game logic
memory to another region which the SA-1 system can access and modify. In
addition to that, a lot of the game routines are slight edited to call the SA-1
CPU during the most heavy operations and even make some of the routines run in
parallel (SNES and SA-1 executing code at the same time, in parallel). Together
that, some of the game enhancements involves some more deep modifying of the
game engine, for example, the More Sprites enhancement, which expands the
maximum number of sprites to 22 or the level limits expander, which makes it
possible to have up to 255 sprites on a single level and much more...

Fortunately, that does not mean there will be game bugs. Although the patch is
extremely complex, extensive tests and verifications have been done and the
patch is stable and completely functional. In addition to that, when bugs are
found they can be easily fixed without requiring making a new ROM port and
updates are warranted to come quickly, as soon as possible when one finds a
certain bug in most of the games.

The main implications when using the SA-1 patches are resource and emulator
incompatibilities.

## Resource Compatibility

Any patch or tool made for editing Super Mario World must be designed to detect
the presence of the SA-1 Pack and behave properly when the system is present on
the ROM. The resource is responsible for using the correct memory mapping, RAM
remapping and for calling the SA-1 CPU on its code, without having to the user
manually modify it.

Tools made for editing graphics and music are exempt from this, unless if they
edit the ROM directly as well.

Sprites and blocks must be converted for SA-1 compatibility as well, but you
can download the SA-1 Convert Tool which allows converting them automatically
for you.

Overall, the most important is checking for patch and tool compatibility. On
[SMW Central](https://www.smwcentral.net/), you can verify if a certain
resource is compatible or not with SA-1 by checking for the`sa-1`tag in the
submission information.

[Lunar Magic](https://fusoya.eludevisibility.org/lm/index.html) has native SA-1
support since version 2.20.

For more information about converting a certain resource to SA-1 compatibility
manually, check the docs folder and the technical files included, specially the
[Memory Map Summary](/docs/memory-map-summary.md).

## Emulator Compatibility

SA-1 is an enhancement chip used on many SNES games. Although quite popular,
unfortunately the SA-1 chip lacks proper emulation support for some of the
known emulators available to download. Older emulators may not have some of
the chip features implemented or may have unstable, slow emulation which can
make the game slower, unstable or even completely unplayable. It's extremely
important to use an accurate and updated emulator when playing not just
regular SA-1 games, but any SMW hack with SA-1 Pack applied. Currently it's
strongly recommended to play SA-1 games with Snes9x 1.56 and bsnes/higan.
Older or different emulators may not work properly.

ZSNES in particular, while an extremely popular emulator (specially on the
last decade), it lacks many SA-1 features and support, which makes it strongly
**not** recommended to play games with. Although I still make (many) efforts
for keeping reasonable compatibility with ZSNES, there's absolutely no warranty
of performance and stability when playing SMW SA-1 games with it.

SA-1 Pack is fully compatible with real hardware. It works on both hacked SA-1
carts and sd2snes, with a good performance.

For more information about emulator and hardware compatibility, check out the
[Known Issues](/docs/known-issues.md) document.

Installation
============

As far working with SA-1 can be tedious at start, with
the current development and available compatible
resources, it's already doable to pretty much anyone
who got a fair experience with SMW Hacking to use it.

In order to get started, grab a new clean ROM. Japanese
or European versions will not work.

Now, open the ROM in Lunar Magic and expand it to at least
2MB. **Don't** save any level nor do any action on the editor.

After expanding, apply sa1.asm to your ROM, using Asar.

Then feel free to test it with your preferred emulator. If
it works properly, somewhere in your emulator it should
display SA-1, e.g. ROM+RAM+BAT+SA-1 in Snes9x. If you're
unsure, try editing level 106, change sprite header memory
to 0x10 and insert 20 koopas in the level. If all of them
display, then the SA-1 Pack got successfully inserted.

Now you can apply all other patches/tools that should run
before Lunar Magic. Remember that they should have SA-1
compatibility or else they will corrupt your ROM.

After it, you can finally use Lunar Magic with your ROM.
Remember to use at least version 2.20+.

To enable the double (22 sprites) system, don't forget
to change your sprite header memory to 0x10, except in
boss battles (they doesn't work with that header setting).

Important: If you change the decompression option on
Lunar Magic, you must reapply sa1.asm to your ROM so
the proper GFX decompression routine is used.

This is important for fast level decompression and
compatibility with advanced resources.

Bowser: You must go to level 1C7 and change sprite header
to 0x00, because the default sprite header (0x10) doesn't
work with it and the player will get glitches and stuck after
beating Bowser.

F.A.Q
=====

<dl><dt>
 Q: Is it really hard to work with SA-1?
</dt><dd>
 A: I would say yes, but after some time you'll be able
to see the benefits from using this SA-1 pack. :)
Also once you learn how to make something SA-1
compatible, everything will become easier to work with.
</dd>
<dt>
 Q: Really?
</dt><dd>
 A: The above Q/A was made in 2012. Today, 5 years after,
I still would say it's hard, but not that anymore. There's
much more resources available today.
</dd>
<dt>
 Q: When I edit my ROM in Lunar Magic and open it, the
ROM glitches during the Title Screen. What's going on?
</dt><dd>
 A: Your Lunar Magic version isn't compatible with SA-1 Pack.
</dd><dd>
 Please update to at least version 2.20.
</dd>
<dt>
 Q: When I expanded my ROM to 8MB, ZSNES can't open
anymore.
</dt><dd>
 A: ZSNES doesn't support 8MB ROMs, only up to 6MB. Try
restoring your ROM to a previous state using Lunar Magic
or with a backup. You can though try FuSoYa's custom ZSNES build,
but of course all hackers would need to use too.
</dd>
<dt>
 Q: Whenever I apply a patch to my ROM, it crashes.
</dt><dd>
 A: Make sure that the patch is SA-1 compatible. You can
find a list of SA-1 compatible patches on "Links" section.
Also on SMWC, SA-1 compatible patches will have the "sa1" tag.
</dd>
<dt>
 Q: Whenever I use any tool, the ROM crashes too.
</dt><dd>
 A: Make sure that the tool is SA-1 compatible. Compatible
tools will have the "sa-1" tag on the SMW Central sections.
If the tool you're looking for, try asking for help in the
forums for guidance.
</dd>
<dt>
 Q: If I insert a custom block or custom sprite, the
ROM crashes or glitches when the block/sprite is present.
</dt><dd>
 A: Blocks and sprites may need to be converted to SA-1.
If case the one you downloaded is not compatible with SA-1,
you can use the SA-1 Convert tool to automatically those
for you.
</dd>
<dt>
 Q: How I can make something compatible with SA-1?
</dt><dd>
 A: Check section "Programming". You will find all
the informations needed for that :)
</dd>
<dt>
 Q: If I change "Compression Options for this ROM" in
Lunar Magic, the ROM gets a little slower on loading. Why?
</dt><dd>
 A: You have to reapply sa1.asm after you change the
compression option, since SA-1 processes that specific part
and it needs a specific decompresser to work property.
</dd></dl>

Credits
=======

SA-1 Pack wouldn't be that awesome without help from these people:

* 33953YoShI (LZ2 patch, original Japanese patch inspiration)
* Adam (Testing)
* Arujus (More sprites patch)
* Alcaro (ZSNES detection code)
* edit1724 (LZ2/3 patches)
* Ersanio (LZ2 patch)
* FuSoYa (6-8MB mapping support/idea, LZ3 patch, LM support)
* Koopster (Testing and documentation)
* Lui37 (Testing)
* Min (LZ2 patch)
* smkdan (LZ2 patches and fixing VRAM patch)
* Ripperon-X (Testing)
* Vitor Vilela (That crazy author that did most of the things)
* You (for using it :D)

Read More
=========

There's more documents and information available in the docs sub-folder:

[Programming](/docs/programming.md) is a full guide about the wonderland SA-1
Pack programming and many special features you can use in your ROM hack.
Additionally, how to convert any incompatible resource to SA-1 Pack compatible
resource.

[Notable Changes](/docs/notable-changes.md) is a list of notable changes
between a normal, SlowROM SMW ROM and a SA-1 Pack SMW ROM.

[Known Issues](/docs/known-issues.md) is a list of currently known SA-1 Pack
issues for each known SNES emulator and hardware. Issues varies between
emulator bugs and SA-1 Pack bugs, which are properly marked for each case.

[Memory Map Summary](/docs/memory-map-summary.md) contains a summary about all
memory changes between the normal SMW ROM and the SA-1 SMW ROM, either because
of the SA-1 ROM mapping or SA-1 Pack memory remaps. Worth reading for who is
interested in converting resources to SA-1 format or is interested in
understanding how the patch works.

[BW-RAM](/docs/BW-RAM.md) contains the map of all BW-RAM related addresses and
information about its mapping capabilities.

[I-RAM](/docs/I-RAM.md) contains the map of all I-RAM related addresses and
information about its mapping capabilities.

[W-RAM](/docs/W-RAM.md) contains the map of all SNES WRAM related addresses,
focused in the differences between normal SMW WRAM map and SA-1 Pack WRAM map.

[Sprite Remap](/docs/Sprite-Remap.md) is a summary about all the sprite table
remaps made by More Sprites patch.

[remap.asm](/docs/remap.asm) contains an .asm macro containing all SA-1 Pack
related remaps for using in patches, blocks and sprites.

Useful Links
============

SMW Central: https://www.smwcentral.net/

SNES Dev. Book: https://www.romhacking.net/docs/226/

SA-1 Registers: https://wiki.superfamicom.org/sa-1-registers

My SMWC Profile: https://smwc.me/u/8251
