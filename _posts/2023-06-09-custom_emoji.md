---
layout: page
title: "Tutorial: making a custom emoji for your Jekyll webpage"
categories: Programming
date: 09-06-2023
permalink: "/posts/prgm/custom-emoji/"
---

&nbsp;&nbsp;&nbsp;&nbsp;*Jekyll is probably the most famous static site generator today. It is free, open source and perfect if you need a personal webpage (like the one you are currently reading), or a page dedicated to a project. Many templates exist to help anyone make the best-looking page in a quick and easy way. However, one might want to put an extra personal touch to make the site more memorable and pleasant to navigate. This post proposes a tutorial to integrate custom emojis to your Jekyll webpage.*

## What are we exactly talking about?

&nbsp;&nbsp;&nbsp;&nbsp; What I propose here is a rather simple, straightforward, free and open-source way of integrating custom emojis from a drawing (or any picture) to your Jekyll page. This means that, using a simple change of font, you will be able to type and use your own doodles or images as emojis, completely integrated in your posts, with the same layout, font color ... as any regular character. This is something that interests me, in pursuit of giving a more playful and personal touch to this page (I like the sobriety of the black and white template, but a little twist never hurts). It will also make it more memorable and recognizable.

## Step 1: Doodling

&nbsp;&nbsp;&nbsp;&nbsp; People who know me are aware that one animal is very dear to my heart, for its weird look and its aura of calm and serenity: the sloth. It is then only logical that I decided to pick this animal as the mascot of this page. I decided to draw the face of a little slothy character and the result is the following one:

<p style="text-align:center;"><img src="/blog/assets/img/emo_1.jpg" alt="Emoji doodle" style="width:300px; height: auto;" class="center"/></p>

Variations of this little face will provide me with emojis suitable for all situations, that I will be able to add in the future at will. It is now time to make this drawing digital, by scanning it and sending it to a computer.

## Step 2: Vectorizing

&nbsp;&nbsp;&nbsp;&nbsp; This step requires the help of a software: [Inkscape](https://inkscape.org/). This open-source tool is designed to make vector graphics in an easy way. Vectorizing will make our drawing of choice defined by mathematical statements (instead of pixels) and will be rescalable at will. (Inkscape will be, beyond this tutorial, a great addition to your software library.)

&nbsp;&nbsp;&nbsp;&nbsp; Going in <span style="color: #ffb66c">*File>Open*</span> will enable us to open our scan. Then, going in Path>Trace Bitmap... opens up a window. This window allows us to create a black-and-white vector file from our drawing via the "Single scan" tab. We can adjust parameters there, such as the threshold from which a zone is considered black or white, or the level of details that will be passed to your vector image. After clicking on <span style="color: #ffb66c">*Apply*</span>, the vector image is created on top of the original one, which we can now delete. The result looks like this:

<p style="text-align:center;"><img src="/blog/assets/img/inkscape_screen.png" alt="Screenshot of Inkscape" style="width:300px; height: auto;" class="center"/></p>

&nbsp;&nbsp;&nbsp;&nbsp; One can see on this screenshot the different points of the vector file, as well as the curves that connect them. Now, we can delete any point, move them around, change the shape of any curve, to obtain a satisfying result. (For example, I simplified a bit the cowlick on top of the sloth's head.) When it is the case, one can save the file in <span style="color: #ffb66c">*.svg*</span> format. This way, it can be included in a font.

## Step 3: The font

&nbsp;&nbsp;&nbsp;&nbsp; This step requires the help of another software: [Fontforge](https://fontforge.org/en-US/). It is also free and open-source, and allows to design custom fonts, which can later be used in any document. Once Fontforge is open, we can start a new font by clicking on <span style="color: #ffb66c">*New*</span>. A table appears, with each square corresponding to a character. By importing a vector file for each character, we indicate what drawing should appear when the corresponding character is typed. If we were to design a standard font, we would add a drawing of the letter "A" in the square marked by "A", a drawing of "B" in "B" etc ... Here, we will use this grid to map our emoji to the keyboard.

&nbsp;&nbsp;&nbsp;&nbsp; Double-clicking on any square opens a window. This window enables you to draw directly the corresponding letter, or to import an <span style="color: #ffb66c">*.svg*</span> file. The latter option is done by going in <span style="color: #ffb66c">*File>Import...*</span>, selecting your vector file of choice, and selecting <span style="color: #ffb66c">*Import*</span>. For the present case, I double-clicked on "A", and imported the vector file shown previously. After that, one can just close this window, and the drawing is now visible in the global grid, under "A".

<p style="text-align:center;"><img src="/blog/assets/img/screenshot_fontforge.png" alt="Screenshot of Fontforge" style="width:500px; height: auto;" class="center"/></p>

&nbsp;&nbsp;&nbsp;&nbsp; One can now generate the font file, which will enable the integration of our newly created emoji into documents (via Word, Pages, or any other word processing software), or into a Jekyll website. This is done by going in <span style="color: #ffb66c">*File>Generate Fonts*</span>. I then selected <span style="color: #ffb66c">*TrueType*</span> as a format, which should change the extension of the created file to <span style="color: #ffb66c">*.ttf*</span>. TrueType is a standard for fonts that is widely used and accepted by most softwares. I named the file <span style="color: #ffb66c">*CustomEmoji.ttf*</span>. Now, our emoji is ready to be displayed on our website.

## Step 4: Using it in Jekyll

&nbsp;&nbsp;&nbsp;&nbsp; We are almost done! To use our new emoji font, we need to show it to our software of choice. Many tutorials exist for Word, Pages or LibreOffice. This is done in Jekyll by first including it to the directory where your Jekyll project is. For the present website, I placed the font in <span style="color: #ffb66c">*assets>fonts*</span>, which is where I keep all the special fonts that I want to use for this website. Then, one needs to tell Jekyll where to go to find fonts. This is done by adding the following lines in the <span style="color: #ffb66c">*_config.yml*</span> file:
<pre>
<code>assets:
  sources:
    -assets/fonts</code>
</pre>
Then, the font needs to be included to the layout of our page. This way, one can define a name for the font, and one can simply call the font by this name later on. I chose the name "Custom Emoji" for this font. This is done by modifying the file named <span style="color: #ffb66c">*variables.scss*</span>, which is in the <span style="color: #ffb66c">*_sass*</span> directory. Defining and naming a new font is then done by adding the following lines:
<pre>
<code>@font-face{
	font-family: "Custom Emoji";
	src:url("../../assets/fonts/CustomEmoji.ttf");
}</code>
</pre>
Of course, it is necessary to change the path to your <span style="color: #ffb66c">*.ttf*</span> file according to your setup.

&nbsp;&nbsp;&nbsp;&nbsp; And voilà! In any post written in Markdown, one can call our font named "Custom Emoji", and just type the character "A" in this font, to see our emoji, perfectly integrated in the theme and layout of our Jekyll webpage!

<span style="font-family: Custom Emoji;font-size: 62.0pt;">A</span>

&nbsp;&nbsp;&nbsp;&nbsp; The html line used to change the font locally is the following one:
<pre>
<code> &lt;span style="font-family: Custom Emoji;
font-size: 62.0pt;"&gt;A&lt;/span&gt; </code>
</pre>

&nbsp;&nbsp;&nbsp;&nbsp; It is necessary to locally increase the font size so that the details of the drawing are visible enough. Not only can you now sign your posts in an original way, you can also put links on your emoji!

&nbsp;&nbsp;&nbsp;&nbsp; Wishing you a lot of fun with your new emojis! [<span style="font-family: Custom Emoji;font-size: 62.0pt;">A</span>](https://www.youtube.com/watch?v=dQw4w9WgXcQ)
