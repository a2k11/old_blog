---
layout: post
title: Video Transcoding
---

### Video Transcoding with paperclip-av-transcoder & avconv

During the past month, I have been working on creating an application which
allows users to upload videos.  Video clip sharing applications like vine are
very fascinating and I wanted to create something similar.  I'm using a JavaScript
HTML5 video player to play the videos and Amazon's S3 storage to store the data.
In order to play each MOV file from an iPhone, for example, I need to transcode
it into mp4 format for it to be playable on my video player.  This is one of the
formats a HTML5 video player can play.  After I figured out exactly what I needed
to do to accomplish all this, I then proceeded to understand the function of each
tool.

[Paperclip](https://github.com/thoughtbot/paperclip) is intended as an easy file
attachment library for Active Record.  This is a great tool provided
by thoughtbot and I use it frequently throughout my projects.  It provides a way
to store image files to a file system while being tracked and updated through
a database like Postgresql.  This sounds great but I'm dealing with video
files which require more attention when it comes to settings and formats.
There is a helpful gem called
[paperclip-av-transcoder](https://github.com/ruby-av/paperclip-av-transcoder)
and it is an audio/video transcoder for paperclip.  This gem uses avconv which
is a fast video and audio converter.

Here is a snippet of code and how I was able to make this work:

<pre><code>
  has_attached_file(
    :video,
    path: "/:class/:id/:style/:filename",
    styles: {
      original: { format: "mp4",
        convert_options: {
          output: { strict: "experimental", s: "480x270" }}},
      thumb: { format: "jpg",
        convert_options: {
          output: { strict: "experimental", ss: 1, vframes: 1, s: "120x67" }}}
    },
    processors: [:transcoder]
  )
</code></pre>

I set a custom path to organize the files saved in my S3 storage.  The styles is
where I was able to select specific options.  The strict option with the value
experimental is important for allowing non-standardized experimental things.
The reason for setting this option is because avconv does not fully support
transcoding mp4 videos.  The s option refers to the size.  Now there is a
geometry option which can be written before convert_options in the first layer
of options for a style.  This wasn't working for me.  The convert_options
setting is quite handy because it literally takes whatever options you place
inside its brackets and executes them like in an avconv terminal line.
For example:

~ %> avconv -i input.MOV -strict experimental -s 480x270 output.mp4

Creating the thumbnail was more challenging due to more options to set.  The s
option refers to the position in the video that you want to take the image.
The vframes options sets the number of frames to record which is just one for
an image.  Here is my example:

~ %> avconv -i input.MOV -strict experimental -ss 1 -vframes 1 -s 120x67 output.jpg

At first I was using Amazon's Elastic Transcoder service because I was unable to
figure out this process.  I knew I had to research exactly how avconv worked and
spend time understanding some of the many properties of video files.  There are
a lot of options you can fool around with and I recommend you start there before
jumping into the code.
