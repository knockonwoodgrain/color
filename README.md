Here's a markdown file (going to turn it into a static page) for everything that I've learned color grading. It's a compilation of YouTube videos and other resources.



<!-- vim-markdown-toc GFM -->

* [Software you Need](#software-you-need)
* [Understanding Image](#understanding-image)
    * [Resolution](#resolution)
    * [Frames Rate](#frames-rate)
    * [Bit Rate](#bit-rate)
    * [Chroma Subsampling](#chroma-subsampling)
    * [Bit Depth](#bit-depth)
    * [Video Codec](#video-codec)
    * [Color Space](#color-space)
    * [Gamma Curve / Correction](#gamma-curve--correction)
    * [Log Profile](#log-profile)
    * [RAW Video?](#raw-video)
* [Color Management](#color-management)
* [Color Primaries](#color-primaries)
    * [Lift Gamma and Gain](#lift-gamma-and-gain)
    * [White Balance](#white-balance)
    * [Exposure](#exposure)
    * [Contrast](#contrast)
    * [Saturation](#saturation)
    * [Primaries Done!](#primaries-done)
* [Look Basics](#look-basics)
    * [Split Tone](#split-tone)
    * [Hue v Sat](#hue-v-sat)
    * [Hue v Hue](#hue-v-hue)
    * [Lum v Sat](#lum-v-sat)

<!-- vim-markdown-toc -->

> [!NOTE]
> AVOID Waqas Qazi and his color grading tutorials, they suck, they break, infact he's been banned on the colorists reddit and professional colorist forums for this reason. There are a very few colorists on YouTube that'll actually teach you and show you tools you can trust. You should obviously try to learn as much as possible, but you'll soon realize that the most useful things will be taught by Cullen Kelly and Darryn Mostyn, and most other people will be repeating them or saying the same thing, I'm not saying they're copying them, I'm just saying that they teach very basic and technical things which are just true no matter who is teaching them. They don't teach you taste, they don't teach you specific looks or grades, you'll have to figure all of that yourself. Or you would have to if you didn't have this.

# Software you Need
This Page is for Videos, so the software that I'll be using is [DaVinci Resolve](https://www.blackmagicdesign.com/in/products/davinciresolve) 


# Understanding Image
Videos have a lot of different attributes and qualities to them, most of it defined how much information is captured by the sensor and how much of it is in the file.

## Resolution
The most common one, this one is very usually just advertised by the camera manufacturers themsleves because it's easy to understand. It's simply the amount of pixels in the image. There's a better explaination for all of these, so I'll be linking wikipedia time to time. You'll most probably skip this considering most people know what Resolution is.

Wikipedia Link: [Display Resolution](https://en.wikipedia.org/wiki/Display_resolution) 

## Frames Rate 
This is the amount of images captured per second. Very simple to understand 

Wikipedia Link: [Frame rate](https://en.wikipedia.org/wiki/Frame_rate) 

## Bit Rate
Bit Rate is the amount of data in storage captured per second. Most cameras have different specific amounts and there aren't really any proper set standards for compressed video. The higher the bit rate, the more information you have to process. So you should shoot at the highest bit rate, except that modern cameras are pretty good at compression, and you can get a pretty okay video with lower bitrates as well.

Wikipedia Link: [Bit Rate](https://en.wikipedia.org/wiki/Bit_rate) 

## Chroma Subsampling
This is usually not advertised, because it's complex. When the video is encoded, it's easier to lose color information and keep the luma information, so videos usually just have half the amount of color information as the luma information. It is better explained in the article.

There's multiple formats,
The most common and default format is 4:2:0, for which per 8 pixels there are only 2 colors and 8 different luma values. Most good cameras can shoot 4:2:2 Internally, which is what you should shoot in. Ideally the lesser the subsampling the better. You want as much information as possible.

Wikipedia Link: [Chroma Subsampling](https://en.wikipedia.org/wiki/Chroma_subsampling) 

## Bit Depth
Bit depth is the amount of colors. That's it. How many colors can exist in the video format. Most videos are 8bit (per component, which means 256 red, 256 green, 256 blue). 8 Bit is usually fine, but most higher end cameras provide a higher bitrate. 8 Bit is the lowest we go without just making the video look bad.

Most good cameras now record in 10 bit, which solves the issue of [Dithering](https://en.wikipedia.org/wiki/Dither) 

Wikipedia Link: [Color Depth](https://en.wikipedia.org/wiki/Color_depth) 

## Video Codec
The video codec is one of the most important parts of the video, as the dictates a lot of other attributes for the video. 

Consumer and Professional video and hybrid cameras mostly record in H.264/AVC, which is a very popular but dated format. 
Another popular format is HEVC/H.265, which is referred as different names, but on Sony cameras it's referred to has XAVC-HS, even though it's the same thing.

The difference between h264 and h265 for post production is that h265 files take more processing power compared to h264 files. So your computer might not be able to handle them. Side note, the free version of DaVinci Resolve also doesn't support h265 files, so it's reccomended you just shoot in h264 or Buy/Pirate Resolve.

Wikipedia Link: [Video Codec](https://en.wikipedia.org/wiki/Video_codec) 


## Color Space
The Color Space is just the range of colors and how it's displayed. I'll do an injustice to explaining them properly. But here's what you need to know

Wikipedia Link: [Color Space](https://en.wikipedia.org/wiki/Color_space) 

The default color space that most displays use is:

[Rec709](https://en.wikipedia.org/wiki/Rec._709), It's just the default color space that displays use.

But actually they use
[sRGB](https://en.wikipedia.org/wiki/SRGB)

sRGB has the exact same colors as Rec709, just a different Gamma Curve (discussed right after this)

Most cameras record in their own color spaces which they should refer to when you're setting it, but some just don't (like Fujifilm, which uses Rec2020).
It's important to know what color space you're recording it, since you will need to convert it later into Rec.709.

## Gamma Curve / Correction
The Gamma of the video defines the luminance curve of the video, it doesn't affect the color. Camera sensors record and recieve video in the linear format, which simply means that the amount of light that is captured is not modified and thus it doesn't look like a displayed image. 

A Gamma curve is required to compress and add contrast to the linear image so that displays can, well, display it. The video gamma curve is also called the transfer curve sometimes.

The default gamma curve is 2.2 on most display devices, though in broadcast and television it is Gamma 2.4. Since Gamme2.4 was the most used and popular one, many platforms and videos still prefer Gamma 2.4 as it's upload format. Which is why YouTube really sucks at processing videos that are encoded in Gamma 2.2, since it applies it's own gamma curve and the blacks dip down and the image becomes much darker (personal experience). 

Wikipedia Link: [Gamma Correction](https://en.wikipedia.org/wiki/Gamma_correction) 


## Log Profile
Log profiles are just gamma curves that give a "wide and dynamic tonal range", these aren't meant to be displayed. Which is why it appears so washed out when displayed directly, since it has to capture as much data as it can while it also saves on data (compared to linear) as it still applies a gamma curve.

When referring to Log profiles and cameras, it is also assumed that the color space will be co-related to the gamma curve. 

In Sony Cameras the Log Profile is Slog3, when it actually referres to the   
color space: Sgamut 3 \
gamma: Slog3

In Fujifilm cameras it's
color space: Rec.2020
gamma: Flog

These log profiles are propreitary.

Wikipedia Link: [Log Profile](https://en.wikipedia.org/wiki/Log_profile) 

## RAW Video?
RAW video is just the raw data from the camera sensor, they're huge uncompress video files, which haven't even been debayered.

This is the most amount of data you can get out of your sensor, because it is all of it. Most cameras now shoow in RAW stills / photos, but not RAW Video.

Only very high end cameras shoot in RAW Video internally, and extremely high end cameras don't even shoot internally, and you need to connect them to external displays and all that stuff I'm not getting into it.

Your camera probably doesn't shoow RAW, because if it does, you mostly know about everything above this and probably a fair bit of what's to come.

Wikipedia Link: [Raw Image Format ](https://en.wikipedia.org/wiki/Raw_image_format) 


# Color Management
The first thing you need to understand after getting your footage is color management.

On Higher end cameras you will have the option to shoot on ["Log"](https://en.wikipedia.org/wiki/Log_profile), as discussed before.

The entire page referres to Davinci Resolve, but I will mostly be discussing the color page. This is a pretty nice first time guide

[DaVinci Resolve Beginners Tutorial: Edit like a PRO for FREE!](https://www.youtube.com/watch?v=SrJOE2pEp7A) 

Now, lets get to the color page.

You'll need to understand how the color page works first.

[Color Page Basics](https://youtu.be/YbDRl_xugJo) 

Then you'll need to understand what color management is, which is the crux of everything pretty much.
This is where you'll know how to convert your Log Profiles to Rec709 Gamma2.4.
So your output will look correct on the screen, like any other normal Video.

[Color Managment EASY!](https://youtu.be/c4AVwVdKTHc) 

Once you understand color management, this tutorial only shows how to do it automatically, but here's the next one

[Color Space Transform - PRO COLORIST Explains](https://www.youtube.com/watch?v=CtSBVKmHkjU) 

Here, you'll understand how you can group your clips according to your color space, and then use these groups to do the color transforms.

It also shows something extremely imporant, which is your working color space. Your working color space (and gamma) is where the grade is applied, and in Resolve, your working color space should be

DaVinci Wide Gamut

and the working gamma would be

DaVinci Intermediate

This is a huge color space and gamma made by Blackmagic for colorists to grade in. 

Now, once you're using groups to assign your color space, and using color space transforms (better than colormanagement), you're ready to go to the next step.

[Pro Colorist Explains: CSTs vs Resolve Color Management](https://www.youtube.com/watch?v=QCRVwkhxDzw) 

For another explaination.

# Color Primaries
Here you'll learn how to adjust the most basic settings for an image. 

Primary adjustments are simply the adjustments that you apply to the entire image. They are broad adjustments that don't apply any kind of look to the image.

## Lift Gamma and Gain
The most basic luminance controls in the program, the big 3 circles out of the big 4 circles in the color grading tab, here's what they do.

[Unlocking the Secrets of Color Grading: A Beginner's Journey with Lift, Gamma, & Gain](https://www.youtube.com/watch?v=Gz_QzBdHDYc) 

## White Balance
White balance is one of the first adjustments you want to make to get the correct footage. It is also the one that requires you to be sensitive and cautionary, because even small adjustments can make skin and other colors look wonky and out of place. Resolve comes with it's own set of tools to adjust while balance, but those tools just fucking suck. I don't know why Resolve keeps doing this and you have to create your own way around to get what you actually want. Here's what you actually want. 

[I stole this trick from VFX artists](https://www.youtube.com/watch?v=3I58NtmWOmE) 

Yeah, it's just gain in the linear gamma, which is the gamma that your camera shoots in, so it's going to be the exact same as adjusting it in camera.

Here's something really important, when you're shooting video YOU REALLY WANT TO MANUALLY SET WHITE BALANCE, which means NO AUTO WHITE BALANCE. Don't do it, no one in the industry does it, they don't do it on film sets, they don't do it when making short films, or advertisements or any of it. You always want to set it manually. 

When I'm shooting in the day I set it to 5200K, or there's probably a daylight setting on your camera, I prefer setting the kelvin amount because it's more predictable and consistent across cameras.

Wikipedia Link: [Color balance](https://en.wikipedia.org/wiki/Color_balance) 

## Exposure
You can adjust exposure after or before white balance, whichever way you prefer, it's going to look the same. I adjust the exposure after white balance.
Most people assume that the way to adjust exposure is with the offset wheel, but this is actually not the case. 

This video will explain why, but it simply referres to what I wrote before, that camera data is recorded in the linear format, so to adjust the exposure, it would also have to be in the linear format.

[This is 80% of what makes your image look great (use it well)](https://www.youtube.com/watch?v=Dnxz5R9HrVA) 

I know that it's a long video, but it's definitely worth the watch.

I personally adjust contrast in a different node, it just makes more sense to me and if I actually want to turn both of them on and off, you can just do it by selecting both of them and turning them on and off.

## Contrast
That was exposure and contrast, though, here's the thing with contrast. You want to be able to adjust the contrast of the video, without affecting the saturation of it.

[Build Your Resolve Toolkit for Perfect Contrast](https://www.youtube.com/watch?v=-3CyJ9EubF8) 

Now, you'll see, adjusting the contrast without adjusting the saturation is possible, but it is better to do so with another method. I'd reccomend that you right click on the node > Blending Mode > Lumninance Only.

Something like that, so you only adjust the luminance of the Image.

## Saturation
The next thing you want to adjust is saturation.

This video is very worth watching

[The best (and worst) saturation tools & techniques in Resolve](https://www.youtube.com/watch?v=5y8TU8UfTAk) 

This video is genuinely amazing, because this kinda shows a lot of what Resolve doesn't show you, the reason why Resolve has so many different sliders and controls for the same operation.

This, HSV sat thing is such a "huge discovery", that every other wannabe influencer colorist will have a reel about "UNLOCKING THE SECRET SAUCE TO SATURATION", and it's the most basic HSV tool, which isn't even the best tool mind you. But yeah color slice is your best bet in the free version of Resolve.


## Primaries Done!
That's all the primaries. That's going to be most of the color grade. 

You might notice that your footage doesn't look very much different, if not different at all. This is because color grading isn't the same as look development.

Look development is applying a look to your image, so it looks a certain way (haha), most professional colorists apply the exact same look right before their ODT (output device transform) AKA the output Color Space Transform to your Display color space.

Some colorists also just use a modified Ouput Device Transform such as [Genesis](https://cullenkellycolor.com/genesis), or something like [OpenDRT](https://github.com/jedypod/open-display-transform). I use OpenDRT myself because it gives a much better image to grade with.

> [!NOTE]
> for both of them you need to have the paid version of Resolve, which is DaVinci Resolve **Studio**

# Look Basics
When you start of wanting to build a look, you'd want to start with the bascis of what makes a look. What adjustments make the image look a certain way. I'm going to start with very simple adjustments and then get to complex ones as I go. This is going to be the crux of what I learned and what adjustments I use.

There is also going to be a lot of relearning through this, as I go from simple techniques to much advanced tools that can only be used in the paid version of Resolve. 

I'm going to start off with basics that only affect color and luminance, and then move on to spatial and textural adjustments.

Now you have to remember that all of these adjustments MUST come after the primaries.

## Split Tone
One of the biggest and easiest adjustments you can apply to your image that will give it a look will be split toning. Very simply put, you're just adjusting your shadows and highlights towards a certain tone. This video here explains it pretty well. You don't want to be using the third technique for this usually.

[The Teal and Orange Look: Pro Colorist Reveals 3 Techniques to Do It Right](https://www.youtube.com/watch?v=cWTprEe5AJg) 

That's literally it. That's the best way to do it. It's a little difficult and it's going to take paitience and time to build these. But they'll be worth it.

I usually use Teal and Orange, Green and Orange (warmer look), Magenta (shadows) and Green (highlights), really good for foliage and looks amazing. Red (shadows) and Cyan (Highlights), cooler fujifilm like adjustment. 

You'll need to experiment and build your own adjustments and preferences. It's going to be a lot of fun.

## Hue v Sat
Another very simple adjustment that can give you great results is the Hue v Sat adjustment. Which simply means adjusting the Saturation based on the hue of the pixel / image. The hues consist of 6 main vectors which you'll be adjusting: Red Yellow Green Cyan Blue Magenta. That's it. Those should be specific enough for you to be adjusting when you're creating your look.

This will help you out a lot in balancing different colors specifically without affecting the entire image, which is the reason it is a **secondary adjustment**

Something very simple and interesting I noticed is that when you're trying to emulate film, reducing the saturation in Red, Green and Blue helps a lot in making it look more like film. I don't really prefer to reduce the saturation in Red though as it affects skin, keeping it mostly intact, while reducing quite a bit of saturation in blue and green for a more filmic look, as it reduces garish colors and creates a more balanced and pleasing image when handling foliage and highly saturated blue tones.

But as it goes with look development, you're free and encouraged to try as many combinations as you like to get what you desire.

## Hue v Hue
This is the adjustment that most people love chasing and changing, because it makes the image look hugely different in a nice way. Though there is a catch to this tool which is that it's very easy to break your image if you adjust a very specific target, or if you adjust one hue beyond another hue, which can cause a hue fold.

But you'll realize that you're making a mistake before it gets that far, because the image will break. 

Now you can go crazy! 

For emulating film, again the very simple thing to do is just understand that colors tend to go towards cyan, magenta and yellow, though it's not as obvious as it sounds.

Simply put, you can adjust your lime greens and yellows to be a little more orange, without touching skin tones. Similarly you can push your greens towards cyan, and your blues towards cyan as well. Making skies look better and your foliage cooler and more appealing. This also creates a very nice contrast in foliage as it expands and seperates it into yellows and cyans. (don't go too crazy with these adjustments). You can also turn your reds very slighly orange, you will notice how that fixes bright red objects and makes your skin looks more natural.

Try to make sure that your skin remains unaffected, so keep your orange intact and never change it's hue. 

This is just what I think you should try out, but you should actually try out everything that you want! GO HAM!

## Lum v Sat
This is another adjustment that you can make that'll give your image a very different look. Which is just adjust the saturation of your image based on the luminance of it. 

You need to remember that you mostly want to reduce saturation here, rather than increase it, because when you increase saturation using this, you're doing so in an additive way, rather in a more natural subtractive way. On the other hand, when you reduce saturation, you do so in a subtractive way, which is what you want.

I usually just reduce saturation in my highlights which makes my image looks much better, as it takes out garish colors and gives the image better color seperation. Overdoing this effect also leads to a sort of bleach bypass effect, which is great if that's what you're looking for. You can also go around and reduce it in the shadows.

You'll soon realize that adjusting it in the midtones basically just reduces saturation everywhere and that's not really so much different than just turning down saturation using your primaries.

