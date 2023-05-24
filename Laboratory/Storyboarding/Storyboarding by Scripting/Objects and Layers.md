![image](https://github.com/Maks1mio/doc-test/assets/44835662/1811b10e-1e20-4f61-b2c7-82f1d7d13267)


# Objects and Layers
## Objects and Layers

Remember that a storyboard, in its simplest form, is a background animation that plays as the backdrop for a beatmap. You may have noticed storyboards with lyrics rushing in like it’s karaoke, particle fuego creating fireworks of fun, or even spectrum bars that pulsate to the music like it’s a media player visualization. All of these images, whether it’s the lyric of a song or it’s a small little sparkly dot, are graphical objects. In storyboarding, we put graphic objects, often known as sprites, onto the background of the beatmap, then we tell these sprites what to do. This chapter will show you the first half of that process, which is creating these graphic objects into existence.

### Objection!

An object is basically the graphic that we want to display on a storyboard. There are two kinds of graphics an object can be created from: a single image file, called a sprite, or a series of image files, called an animation. While animations do have their own uses (such as a character running from one side of the screen to the other), storyboarders overwhelmingly create sprites, as all they need is one single image to create magic.

*#hint*( In this day where game making has become more and more accessible, the term sprite has become a lot more commonplace. Consider a storyboard sprite the exact same thing as the one you may heard of in game design.  Actually, do you happen to know the origin of the word sprite? It’s not because of the soft drink, you know! Back in the early 1980s, for drawing efficiency, sprites were on a separate level than the background when being rendered. Their “floating” overlap was a lot like the mythical sprite, or a ghost. There you have it! )

## Let’s Make An Object!
Let’s start off by creating a sprite! To create a new sprite, you’d write the following line within your .osb file: .. code-block:: c

<div class="code-container">
    <div class="svg-icon"><img src="lib/svg/laboratory/browser-code.svg" alt=""></div>
    <pre><code id="text-to-copy-1" class="language-csharp">Sprite, <<span>layer>, <</span>origin>, <<span>filepath>, <<span>x>, <<span>y></code></pre>
    <button class="copy-button" data-input-id="text-to-copy-1" type="button"><img
            src="lib/svg/laboratory/content-copy.svg" alt=""></button>
</div>
        
Where...
- `<layer>`: The [layer](https://osb.moe/learn/docs/storyboarding/glossary/#term-layer) you want your sprite to appear on.
- `<origin>`: The place on the image the (x,y) position will be based on.
- `<filepath>`: The filename of the image you want.
- `<x>, <y>`: The (x,y) coordinates of where you want to sprite to appear.

Let’s break it down further. If you have a good idea about this stuff already, you can [skip to where we’re going to put things together](https://osb.moe/learn/docs/storyboarding/scripting/objects_and_layers/#applying). After each section, we’re going to slowly replace each one of these items with an example, all totaling to a bona-fide, legit sprite that we can use and play around with!

### Layers: Stack ‘Em Up

In traditional animation, animators need to draw each frame by hand. However, drawing each Astro Boy frame in some empty void is far easier than drawing him in the sprawls of a bustling city. Imagine the work necessary to redraw both Astro Boy AND the cityscape! So then animators thought up of a clever trick. They painted the city background as one image, then had the moving objects such as Astro Boy or the cars in the city on their own transparent sheets known as cels, then stack them all together, so the camera thinks they’re all one singular image. This is a prime example of layering.

![image](https://github.com/Maks1mio/doc-test/assets/44835662/e310c32f-6b3f-46f2-9fde-6607a49c1416)

In osu!, a layer works exactly the same way. We can assign sprites to certain layers, and then at the very end, they’ll all stack up together.
        
There are four possible layers we can use:
- **Background**
- **Fail**
- **Pass**
- **Foreground**

The only things worth mentioning would be that the fail and pass layers have their own special conditions to appear visible. You can read more about them by clicking on their glossary terms, but at the end of the day, it’s easier to just adopt the mentality of primarily sticking with the background and foreground.
When you have multiple sprites on the same layer, the one created later (i.e. appears later in the script file), will be on top of the previous sprite(s). This is a simple case of what’s called z-order.
Sounds good then! Now that we understand what layers are, let’s fill that placeholder in with a layer of our choice. Let’s go with Foreground.

<div class="code-container">
    <textarea style="display: none;" disabled type="text"
        id="text-to-copy-2">Sprite, Foreground, <origin>, "<filepath>", <x>, <y></textarea>
    <div class="svg-icon"><img src="lib/svg/laboratory/browser-code.svg" alt=""></div>
    <pre><code class="language-csharp" data-input-id="text-to-copy-2"></code></pre>
    <button class="copy-button" data-input-id="text-to-copy-2" type="button"><img
    src="lib/svg/laboratory/content-copy.svg" alt=""></button>
</div>
        
### Origin: It All Starts Here

Before deciding on an initial location you want your sprite to be, run by this thought: when we tell osu! to put a sprite at this numbered location, where exactly is it at? For context, the center of the playfield is at (320,240). If we think a 1x1 image, or a single pixel, at (320,240), that’s easy to imagine, as the pixel is exactly. But consider a 100x100 sprite. What part of the image is exactly at (320,240)? Is it the upper-left of the image? The center?

This is exactly what the origin entails. For what area of the image do we consider to make as a point of reference?

*#Todo*( Add a picture demonstrating the nine origin points of an image. )
        
There are nine possible origin points of an image:
- **TopLeft**
- **TopCentre**
- **TopRight**
- **CentreLeft**
- **Centre**
- **CentreRight**
- **BottomLeft**
- **BottomCentre**
- **BottomRight**

The most likely choice you’d find yourself using is Centre, as calculations such as movement and scale are handled far, far easier than the other settings. However, for special situations, the other origin points are very useful to have. For our example, let’s stick with Centre, then.
        
<div class="code-container">
    <textarea style="display: none;" disabled type="text"
        id="text-to-copy-3">Sprite, Foreground, Centre, "<filepath>", <x>, <y></textarea>
    <div class="svg-icon"><img src="lib/svg/laboratory/browser-code.svg" alt=""></div>
    <pre><code class="language-csharp" data-input-id="text-to-copy-3"></code></pre>
    <button class="copy-button" data-input-id="text-to-copy-3" type="button"><img
    src="lib/svg/laboratory/content-copy.svg" alt=""></button>
</div>
        
### Filepath: Locate Me, Senpai!
        
What image do you want the sprite to display? This is relatively straightforward, but there are a few caveats to keep in mind:
- The filepath is relative to the .OSB file. That means that the mapset’s folder will be the starting location in looking for files. For instance, an image named `"walrus.png"` that’s in the same folder as the storyboard script can simply be called as `"walrus.png"`, with peace of mind.
- When calling for images inside a subfolder of the mapset, you can use the forward-slash (`/`) over the backslash. If `"walrus.png"` is stored inside the `SB` folder, you can just call it through `"SB/walrus.png"` without any problems. While the slashes are converted to backslashes in the end, it saves a lot more time typing a `/` than `\` anyhow.

Those are the biggest concerns!

*#Todo*( Quotation marks surrounding the filepath are also optional! However, if your path location to your sprite requires spaces, the quotation marks become required to use. Keep that in mind! )

In that case, we can just move on our example with grabbing a lovely sprite of Hifumi.

<div class="code-container">
    <textarea style="display: none;" disabled type="text"
        id="text-to-copy-4">Sprite, Foreground, Centre, "<SB/hifumi.png>", <x>, <y></textarea>
    <div class="svg-icon"><img src="lib/svg/laboratory/browser-code.svg" alt=""></div>
    <pre><code class="language-csharp" data-input-id="text-to-copy-4"></code></pre>
    <button class="copy-button" data-input-id="text-to-copy-4" type="button"><img
    src="lib/svg/laboratory/content-copy.svg" alt=""></button>
</div>

### Coordinates: X Marks the Spot!
        
Assuming that you haven’t slept through any basic algebra class, you must be familiar with the concept of the coordinate plane, or that two-dimensional graph that charts points on horizontal and vertical axes known as X and Y. In a math class, however, the traditional Cartesian coordinate system has the origin point, or (0,0), as some center point between four quadrants, with increasing values moving right and upwards, and decreasing values going left and downwards. However, video game coordinates tend to work differently, and the coordinate system for osu! is no different.

In osu!, for a 4:3 screen, this origin point (0,0) is at the top-left of the screen, or the top-left of the playfield. While X behaves exactly the same way with increasing values moving rightwards and decreasing values going leftwards, a higher Y value will go downwards, and a lower Y value will go upwards instead. The screen’s boundaries max out to 640x480 for a 4:3 screen, meaning that anything outside the range from 0-640 and 0-480 for the X and Y values respectively are considered off-screen (though if the sprite is large enough, it may only be partially off-screen).

![Figma_SmgZWA5Xkb 2](https://github.com/Maks1mio/doc-test/assets/44835662/d1a3599c-558d-45a3-83c3-45ddccd944c9)
> Photoshop also shares this coordinate system when treating pixels on an image, as shown in this example image.

When osu! moved on to support 16:9, or widescreen, storyboards, the overall screen size expanded to 854x480. However, to ensure backwards compatibility with existing storyboards, the origin point of (0,0) remained exactly at the same spot, and rather, additional pixels were opened to the left and right instead. This expanded the visible screen to go from -107 to 747 for X.

So to summarize, here are the important values to take from this:
- Increasing X values move rightwards. Increasing Y values move downwards.
- The viewport range for a 4:3 storyboard is 0-640 for X and 0-480 for Y.
- The viewport range for a 16:9 storyboard is -107-747 for X and 0-480 for Y.
- The center of the screen is (320,240).

*#Todo*( Are these numbers arbitrary!? How did you find out these numbers!? Consider the center point, 320. Half the screen size for 16:9 is `854/2`, or 427. Subtract or add this value to 320, and you’d get -107 and 747 respectively. Pretty cool, right? )

So with all of this coordinate talk, we’ll just cop out and have the sprite centered. Easy enough, right?

<div class="code-container">
    <textarea style="display: none;" disabled type="text"
        id="text-to-copy-5">Sprite, Foreground, Centre, "<SB/hifumi.png>", 320, 240</textarea>
    <div class="svg-icon"><img src="lib/svg/laboratory/browser-code.svg" alt=""></div>
    <pre><code class="language-csharp" data-input-id="text-to-copy-5"></code></pre>
    <button class="copy-button" data-input-id="text-to-copy-5" type="button"><img
    src="lib/svg/laboratory/content-copy.svg" alt=""></button>
</div>

### All Together Now...
*#Todo*( Summarize all the sections mentioned in Objects & Layers to this collective point. )

### Animations
*#Todo*( Similar to how sprites work, write about how animations work and provide an example. )

### To Summarize...
*#Todo*( Are these numbers arbitrary!? How did you find out these numbers!? Consider the center point, 320. Half the screen size for 16:9 is 854/2, or 427. Subtract or add this value to 320, and you’d get -107 and 747 respectively. Pretty cool, right? )

![image](https://github.com/Maks1mio/doc-test/assets/44835662/d40329e3-1127-443a-a9c2-e308cf43d8ab)
